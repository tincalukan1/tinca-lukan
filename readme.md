# Navodila za nastavitev osebne Hugo strani laboratorija

V tem dokumentu so navedena navodila, kako nastaviti in uporabljati svojo Hugo stran za laboratorij. Vsak član laboratorija bo imel svojo Hugo stran, ki bo gostovana pod domeno **sujtfri.github.io/member_repository**.

## 1. Kopiranje predloga repozitorija

### A. Kako uporabiti privzeti predlog

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite [predlogo Hugo strani](https://github.com/sujtfri/member_template), ki je na voljo v repozitoriju.
6. Kliknite gumb **Use this template**.
7. Ustvarite novo ime za vaš osebni repozitorij. Priporočljivo je, da uporabite svoje osebno ime, na primer: **ime.priimek** ali **ime-priimek**
8. Preverite, da je izbrana možnost Public repository, ter da je **owner sujtfri** in kliknite Create repository

### B. Kako omogočiti drugim članom uporabo vašega repozitorija kot predloge

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite vaš repozitorij, ki ga želite omogočiti kot predlogo.
3. Pojdite na **Settings** (nastavitve) vašega repozitorija.
4. Pomaknite se navzdol do razdelka **Template repository** in označite možnost **This repository is a template**.
5. Kliknite **Save changes**.

Po tem bo vaš repozitorij na voljo kot predloga za druge člane laboratorija.

### C. Kako uporabiti repozitorij drugega člana kot predlogo

1. Prijavite se v GitHub in pojdite na GitHub organizacijo laboratorija.
2. Odprite repozitorij, ki ga želite uporabiti kot predlogo.
3. Kliknite gumb **Use this template**.
4. Ustvarite novo ime za vaš osebni repozitorij. Priporočljivo je, da uporabite svoje osebno ime, na primer: **ime-priimek**.
5. Preverite, da je izbrana možnost **Public repository**, ter da je **owner sujtfri**, in kliknite **Create repository**.

## 2. Kloniranje repozitorija

### 1. Odprite terminal ali ukazno vrstico in klonirajte svoj novoustvarjeni repozitorij na lokalni računalnik:

```bash
git clone https://github.com/sujtfri/ime-priimek.git
```

### 2. Premaknite se v imenik repozitorija:

```bash
cd ime-priimek
```

### 3. Omogočanje GitHub Pages in GitHub Actions

1. Pojdite na nastavitve vašega repozitorija v GitHub.
2. Izberite zavihek **Pages**.
3. V razdelku Source izberite **GitHub Actions** kot vir za GitHub Pages.

### 4. Inicializacija teme kot podmodula

Po kloniranju repozitorija in premiku v imenik, morate inicializirati podmodul teme:

```bash
git submodule update --init --recursive
```

Ta ukaz prenese temo, ki je potrebna za delovanje Hugo strani. Če v prihodnosti pride do posodobitev teme, lahko uporabite ukaz:

```bash
git submodule update --remote
```

## 3. Urejanje osebne vsebine

Vse spremembe boste izvajali znotraj svojega repozitorija. Vaša osebna stran v Hugo je zasnovana tako, da omogoča preprosto upravljanje vsebin. Spodaj so podana navodila za pisanje objav in nastavitev strani. Pri urejanju vsebine v Markdownu lahko uporabite HTML v Markdown converter-ji, kot je npr. **[https://htmlmarkdown.com/](https://htmlmarkdown.com/)**, če imate vsebino v HTML obliki, ki jo želite pretvoriti.

### 3.1. Urejanje glavne biografije

Glavna biografija vsakega člana je v datoteki **content/\_index.md**. Ta datoteka predstavlja vašo domačo stran in vsebino, ki bo vidna ob obisku vašega profila.
V primeru **večjezične vsebine** se glavna biografija nahaja v datotekah, specifičnih za posamezen jezik. Na primer:

- Za angleško različico: **content/english/\_index.md**
- Za slovensko različico: **content/slovene/\_index.md**

#### Kako urediti biografijo:

1. Odprite datoteko **content/\_index.md** (ali ustrezno datoteko za vaš jezik).
2. Vnesite ali uredite svojo biografijo. Uporabite Markdown za formatiranje besedila.

Primer vsebine:

```markdown
+++
title = "Ime Priimek"
+++

# Dobrodošli

Sem Ime Priimek, raziskovalec v Laboratoriju za kognitivno modeliranje.
```

### 3.2. Ustvarjanje novih strani

Vsaka dodatna stran, ki jo želite imeti na svojem profilu, potrebuje svojo mapo in datoteko \_index.md.

#### Koraki za ustvarjanje nove strani:

1. Če želite ustvariti novo stran, na primer **"Lecturing"**, ustvarite naslednjo strukturo:
   - **content/lecturing/\_index.md** (ali ustrezno datoteko za vaš jezik, npr. **content/english/\_index.md**)
2. Za vsako podstran znotraj te strani (npr. posamezni predmeti) lahko ustvarite dodatne datoteke, na primer:
   - **content/lecturing/subject1.md** (ali ustrezno datoteko za vaš jezik, npr. **content/english/lecturing/subject1.md**)

#### Primer nove strani **"Lecturing"**

```bash
hugo new content/lecturing/_index.md  // hugo new content/english/lecturing/_index.md
```

#### Vsebina **content/lecturing/\_index.md**:

```markdown
+++
title = "Lecturing"
+++

# Moji predmeti

Tukaj so navedeni predmeti, ki jih predavam.

1. [Subject 1]({{< relref "subject1.md" >}})
2. [Subject 2]({{< relref "subject2.md" >}})
```

#### Vsebina **content/lecturing/subject1.md**:

```markdown
---
title = "Predmet 1"
---

# Opis predmeta 1

Podroben opis predmeta.
```

### 3.3. Dodajanje datotek in slik

Vsaka stran na vašem profilu naj vsebuje pripadajoče datoteke, kot so slike, v isti mapi, kjer se nahaja vsebina strani. Na ta način bodo slike in druge datoteke ustrezno povezane s posamezno stranjo.

#### Koraki za dodajanje slik na stran:

1. Če želite dodati sliko na stran, na primer na glavno stran Lecturing (content/lecturing/\_index.md), morate sliko shraniti v isto mapo.

- Primer: **content/lecturing/img.jpg** ali **content/lecturing/images/img.jpg**

2. Nato v vaši Markdown datoteki (npr. **content/lecturing/\_index.md**) vključite sliko z naslednjim ukazom:

```markdown
![Opis slike](img.jpg)
ali
![Opis slike](img/img.jpg)
```

#### Dodajanje datotek in slik neposredno iz OneDrive:

1. Če želite dodati slike ali datoteke iz OneDrive, pojdite na svojo datoteko v OneDrive in ustvarite **embed** link.
2. To storite tako, da v OneDrive izberete datoteko, ter na vrhu strani izberite **Embed**.
3. Kopirajte in prilepite povezvo v svojo markdown datoteko.

Primer:

```markdown
![FRI logo](https://1drv.ms/i/s!AnTtkNv__VGYgmWLhKoip-3jZL0j?embed=1&width=620&height=259)
```

![FRI logo](https://1drv.ms/i/s!AnTtkNv__VGYgmWLhKoip-3jZL0j?embed=1&width=620&height=259)

### 4. Urejanje datoteke hugo.toml

Vsakič, ko dodate novo stran, morate posodobiti datoteko hugo.toml, da se nova stran prikaže v meniju. Poleg tega morate prilagoditi naslov, baseURL, in meni.

#### Koraki za urejanje:

1. Odprite datoteko **hugo.toml** v korenu svojem repozitoriju.
2. Spremenite osnovne nastavitve strani:
   - **baseURL**: Tukaj vnesite URL vašega repozitorija. Nadomestite ime-priimek z imenom vašega repozitorija.
   - **title**: Vnesite naslov svoje strani.
   - **menu**: Dodajte nove strani v meni.

#### Dodajanje novega menija:

Če želite dodati novo stran v meni, na primer za "Raziskave", ki se nahaja v **content/research/\_index.md**, v datoteko hugo.toml dodajte nov vnos:

```toml
  [[menu.main]]
    name = "Raziskave"
    url = "/research/"
    weight = 4
```

#### Primer urejene datoteke **hugo.toml**:

```toml
baseURL = 'https://sujtfri.github.io/ime-priimek/'  # Spremenite ime repozitorija
languageCode = 'en-us'
title = 'Ime Priimek'
theme = "member-theme"

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1

  [[menu.main]]
    name = "Lecturing"
    url = "/lecturing/"
    weight = 2

  [[menu.main]]
    name = "Projekti"
    url = "/projects/"
    weight = 3

```

#### Urejanje datoteke hugo.toml za večjezično vsebino

Če želite omogočiti večjezično podporo za svojo stran, boste morali nastaviti jezike v datoteki hugo.toml. V spodnjem primeru so nastavljeni jeziki za angleščino (en) in slovenščino (si).

Primer za angleški in slovenski jezik:

```toml
baseURL = 'https://sujtfri.github.io/ime-priimek/'  # Spremenite ime repozitorija
title = 'Ime Priimek'
theme = "member-theme"
[languages]
  [languages.en]
    contentDir = 'content/english'
    languageName = 'English'
    weight = 10
    [languages.en.params]
      flag = "flag-icon-us"
    [languages.en.menus]
      [[languages.en.menus.main]]
        name = "About"
        url = "/"
        weight = 100
      [[languages.en.menus.main]]
        name = "Lecturing"
        url = "/lecturing/"
        weight = 200
      [[languages.en.menus.main]]
        name = "Projects"
        url = "/projects/"
        weight = 300

  [languages.si]
    contentDir = 'content/slovene'
    languageName = 'Slovene'
    weight = 10
    [languages.si.params]
      flag = "flag-icon-si"
    [languages.si.menus]
      [[languages.si.menus.main]]
        name = "O meni"
        url = "/si/"
        weight = 100
      [[languages.si.menus.main]]
        name = "Poučevanje"
        url = "/si/lecturing/"
        weight = 200
      [[languages.si.menus.main]]
        name = "Projekti"
        url = "/si/projects/"
        weight = 300
```

V tem primeru so nastavljeni jezikovni nastavitvi za angleščino in slovenščino z ustreznimi mapami za vsebino **content/english** in **content/slovene**. Vsak jezik ima svojo kodo zastave (npr. flag-icon-us za angleščino in flag-icon-si za slovenščino). Vsak jezik ima tudi svojo različico menija, kjer so se imena strani prevedena v ustrezni jezik.

Navodila za večjezične strani:

1. Ustvarite mapo za jezik: V glavni mapi content ustvarite mapo za vsak jezik, na primer **content/english** za angleščino in **content/slovene** za slovenščino.
2. Ustvarite vsebino za vsak jezik: Za vsako stran, ki jo želite prevesti, ustvarite različico v ustrezni jezikovni mapi. Na primer, stran about.md bo v **content/english/about.md** in **content/slovene/about.md.**
3. Dodajte ustrezne povezave: Prepričajte se, da so vsi meniji pravilno nastavljeni v hugo.toml za vsak jezik.

## 4. Testiranje lokalnih sprememb

Preden pošljete svoje spremembe v GitHub, je priporočljivo, da svojo stran preizkusite lokalno z ukazom Hugo, kar vam omogoča hitrejši pregled in odkrivanje morebitnih napak.

### 4.1 Uporaba "hugo server"

Ukaz **"hugo server"** vam omogoča, da zaženete lokalni strežnik, kjer lahko pregledate svojo stran, ne da bi jo objavili.

**Kako uporabiti hugo server:**

1. Odprite terminal ali ukazno vrstico v korenskem direktoriju vašega Hugo repozitorija.
2. Zaženite naslednji ukaz:

```bash
hugo server
```

Ta ukaz bo ustvaril lokalni strežnik, ki bo na voljo na naslovu http://localhost:1313/. Stran bo samodejno osvežena, če boste v datotekah izvedli spremembe. To vam omogoča hitrejše testiranje vsebine.

#### 4.2 Uporaba "hugo server -D"

Ko razvijate novo vsebino, lahko želite testirati strani ali objave, ki še niso objavljene, ker so označene kot osnutki. V ta namen uporabite ukaz **"hugo server -D"**, ki omogoča prikaz osnutkov.

**Kako uporabiti "hugo server -D":**

1. Če imate osnutke, ki jih želite pregledati pred objavo, zaženite naslednji ukaz:

```bash
hugo server -D
```

S tem ukazom bodo vidne tudi vse strani ali objave, ki imajo v svojem frontmatter parametru draft = true.

#### 4.3 Kaj pomeni parameter "draft"?

V vsaki objavi ali strani, ki jo ustvarite v Hugo, lahko uporabite parameter draft, ki določa, ali je stran pripravljena za objavo ali je še v fazi osnutka.

Primer parametra **draft** v frontmatter:

```markdown
+++
title = "Moj prvi projekt"
date = 2024-10-10
draft = true
+++
```

- Če je **draft = true**, bo stran skrita in ne bo objavljena na produkcijski strani.
- Če je **draft = false**, bo stran vidna in objavljena na vaši spletni strani.

Ko ste pripravljeni, da stran objavite, preprosto spremenite vrednost parametra **draft** na **false**, nato pa lahko svojo stran testirate lokalno z hugo server ali naložite spremembe na GitHub.

## 5. Dodajanje profila v glavni repozitorij

1. Pojdite na glavni repozitorij laboratorija sujtfri.github.io.
2. Poiščite datoteko **data/members.yaml**, kjer se hranijo podatki o vseh članih laboratorija.
3. Dodajte svoje podatke, kot v spodnjem primeru:

```yaml
staff_members:
  - name: "Ime Priimek"
    bio: "Vaša kratka biografija."
    image: "img/people/vaša_slika.jpg"
    contact: "vaš_email@example.com"
    relurl: "ime-priimek/"
    phone: vaša telefonska številka
```

4. V datoteko **static/img/people/** dodajte svojo sliko profila. Prepričajte se, da ime slike ustreza tistemu, kar ste vnesli v **data/members.yaml**.

## 6. GitHub Actions: Samodejna gradnja in objava

Ko naredite spremembe na svoji strani in jih naložite v GitHub, ni potrebno ročno graditi strani ali jih nalagati na strežnik. Za to skrbi datoteka z GitHub Actions, ki se nahaja v **.github/workflows/hugo.yaml**.

### Kaj dela ta datoteka:

- Ob vsakem "push" na glavno vejo (**main**) se vaša stran samodejno zgradi in objavi.

- Uporablja Hugo za gradnjo statične strani in jo nato objavi na GitHub Pages.

- Postopek zajema namestitev Hugo, sestavo statične strani in objavo na GitHub Pages, kjer bo vaša stran dostopna.

Zato vam ni treba skrbeti za ročno upravljanje strežnika ali nalaganje strani. Vse se dogaja samodejno ob vsaki spremembi, ki jo pošljete v svoj repozitorij.

## 7. Posodabljanje in objavljanje

Po urejanju datotek in ustvarjanju novih vsebin, zaženite naslednje ukaze, da pošljete spremembe v repozitorij:

```bash
git add .
git commit -m "Dodana nova stran in objava"
git push
```

To bo sprožilo postopek gradnje in objave preko GitHub Actions. Vaša stran bo posodobljena in dostopna na naslovu: https://sujtfri.github.io/ime-priimek/.
