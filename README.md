# W+H CarrySolutions & Services — Website

Statische Website für die Spedition W+H CarrySolutions & Services, Wilhelm-Binder-Straße 19, 78048 VS-Villingen.

Kein Build, kein Framework, keine Abhängigkeiten — reines HTML und CSS. Wer die Seite ändern will,
braucht nur einen Texteditor.

## Dateien

| Datei | Inhalt |
|---|---|
| `index.html` | Startseite — Hero, Leistungen, Direktprinzip, Team, Zahlen, Kontakt |
| `impressum.html` | Impressum |
| `datenschutz.html` | Datenschutzerklärung (Entwurf, siehe offene Punkte) |
| `style.css` | Das gesamte Design, inklusive Farben und Darstellung auf dem Handy |
| `images/hero.jpg` | Großes Bild im Kopf der Startseite |
| `vercel.json` | Saubere URLs (`/impressum` statt `/impressum.html`) und Sicherheits-Header |

## Lokal ansehen

Doppelklick auf `index.html` genügt. Oder mit einem kleinen Server, dann funktionieren auch
die Links `/impressum` und `/datenschutz` so wie später im Netz:

```bash
python3 -m http.server 8000
# dann http://localhost:8000 im Browser öffnen
```

## Auf Vercel veröffentlichen

1. Auf [vercel.com](https://vercel.com) anmelden (der kostenlose Hobby-Plan reicht aus).
2. **Add New → Project** → dieses GitHub-Repository auswählen → **Import**.
3. Bei *Framework Preset* **Other** stehen lassen, Build Command und Output Directory leer lassen.
4. **Deploy**.

Danach veröffentlicht jeder `git push` auf `main` automatisch die neue Fassung.

Eigene Domain: im Vercel-Projekt unter **Settings → Domains** `wh-carrysolutions-services.de`
eintragen und die dort angezeigten DNS-Einträge beim Domain-Anbieter hinterlegen.

## Gestaltung

- **Farben:** Primärblau `#0D5FCE`, helleres Blau `#2B86F0` für Verläufe und Akzente,
  Dunkelblau `#07213F` für die Zahlenleiste, Anthrazit `#1E2630` für die Infokarte und den Kontaktbereich.
  Alle Werte stehen gesammelt ganz oben in `style.css` unter `:root`.
- **Schriften:** *Saira Condensed* für Überschriften, *Barlow* für Fließtext, beide von Google Fonts.
- **Heller und dunkler Modus:** Die Seite richtet sich nach der Systemeinstellung des Besuchers.
- **Handy:** Ab etwa 880 px Breite klappt die Navigation zu einem Menü zusammen, die Spalten stapeln sich.

## Hero-Bild austauschen

Das Bild im Kopf ist **mit KI erzeugt** und zeigt keine echten Fahrzeuge von W+H
(siehe offene Punkte). Austauschen geht so:

1. Neues Foto als `images/hero.jpg` ablegen. Querformat, etwa 2400 px breit, unter 500 KB.
   Breite Formate um 21:9 passen am besten; das Motiv sollte oben in der Mitte ruhig sein,
   weil dort die Überschrift steht.
2. Fertig — der Dateiname ist in `style.css` bereits hinterlegt.

Soll das Bild anders heißen oder ganz entfallen, steht die Zeile in `style.css` im Block `.hero{ … }`:

```css
--hero-photo: url("images/hero.jpg") center/cover no-repeat;
```

Wird die Zeile gelöscht, zeigt der Kopf einen blauen Verlauf statt eines Fotos.
Die dunklen Verläufe über dem Bild bleiben in jedem Fall erhalten, damit die weiße Schrift lesbar ist.

## Texte ändern

Alle Texte stehen direkt in den HTML-Dateien, ohne Redaktionssystem dazwischen. Die wichtigsten Stellen
in `index.html`:

| Was | Suchbegriff in der Datei |
|---|---|
| Überschrift im Kopf | `Ihr Spediteur für` |
| Die drei Kästen unter dem Bild | `class="panel"` |
| Die sechs Leistungen | `class="grid6"` |
| Blauer Abschnitt zum Direktprinzip | `Keine Sammelgutverkehre` |
| Die beiden Personen | `class="person"` |
| Zahlenleiste | `class="facts"` |
| Telefonnummer und E-Mail | `tel:+49` beziehungsweise `mailto:` |

Die Telefonnummer steht an zwei Stellen: einmal als sichtbarer Text, einmal im Link
(`tel:+4916099717921`). Beide müssen gemeinsam geändert werden.

## Offene Punkte

- **Das Hero-Bild ist KI-generiert.** Es zeigt drei blaue Lkw mit der Aufschrift „W+H", aber es sind
  nicht die Fahrzeuge von W+H. Außerdem sind darauf fremde Herstellerembleme (Mercedes, MAN, Volvo)
  und erfundene Kennzeichen zu sehen. Vor einer dauerhaften Nutzung bitte prüfen, ob das gewollt ist —
  ein echtes Foto des eigenen Fuhrparks ist in jedem Fall die bessere Lösung.
- **Weitere echte Fotos fehlen** — Ladung, Hebebühne im Einsatz, ein Bild der beiden Ansprechpartner.
  Handyfotos in guter Auflösung genügen.
- **Logo** liegt nicht als Datei vor. Im Kopf steht derzeit ein gesetzter Schriftzug mit einer
  nachgebauten Bildmarke. Mit der Originaldatei (am besten SVG oder PNG mit transparentem Hintergrund)
  lässt sich das ersetzen.
- **Firmierung bestätigen** — die Seite nennt durchgehend „W+H CarrySolutions & Services" ohne
  Rechtsformzusatz, passend zum Impressum. In den ersten Unterlagen stand abweichend
  „W+S CarrySolutions GmbH".
- **Fahrgebiet** — nur Deutschland oder auch grenzüberschreitend? Steht derzeit nicht auf der Seite.
- **Qualifikation von Lars Hindelang** — in den Unterlagen stand „Fachwirt /" ohne Zusatz.
- **Datenschutzerklärung ist ein Entwurf** und sollte vor dem Livegang rechtlich geprüft werden.
  Die gelb markierten Stellen sind die offenen Punkte.
- **Google Fonts** werden von Googles Servern geladen; darauf weist die Datenschutzerklärung hin.
  Wer das vermeiden will, lädt die beiden Schriften herunter, legt sie in einen neuen Ordner `fonts/`
  und bindet sie per `@font-face` lokal ein — dann entfällt der entsprechende Absatz.

## Was die Seite bewusst nicht tut

Keine Cookies, kein Tracking, keine Analyse-Werkzeuge, kein Kontaktformular. Deshalb braucht die
Seite auch kein Cookie-Banner. Kontakt läuft über Telefon und E-Mail.

Soll später ein Anfrageformular dazukommen, braucht es einen Dienst, der die Einsendungen entgegennimmt —
und dann einen zusätzlichen Absatz in der Datenschutzerklärung.

## Kontakt

Erstellt von Rüb Studio, Marcus Rüb.
