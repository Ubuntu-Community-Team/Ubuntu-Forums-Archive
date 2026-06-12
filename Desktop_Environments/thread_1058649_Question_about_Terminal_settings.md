---
title: "Question about Terminal settings"
date: 2009-02-03
forum: Desktop Environments
---

### Post by kbloem on 2009-02-03
Hello,

Is it possible to give the commandline a different color than the output of those commands?

root@HP-Kenny:/etc/samba# [COLOR="Red"]nano smb.conf[/COLOR] 
root@HP-Kenny:/etc/samba# [COLOR="Red"]mkdir private[/COLOR]
root@HP-Kenny:/etc/samba# [COLOR="Red"]cd private/[/COLOR]
root@HP-Kenny:/etc/samba/private# [COLOR="Red"]touch [/COLOR]
touch: geen bestand opgegeven
Typ 'touch --help' voor meer informatie.
root@HP-Kenny:/etc/samba/private# [COLOR="Red"]touch --help[/COLOR]
Gebruik:  touch [OPTIE]... BESTAND...
Waardeer de toegangs- en wijzigingstijden van elk BESTAND op tot de huidige tijd.

Een BESTAND argument dat niet bestaat wordt leeg aangemaakt.

Een BESTAND argument dat - is wordt speciaal behandeld en zorgt er voor dat touch
de tijden van het bestand geassociëerd met standarduitvoer wijzigt.

(Een verplicht argument bij een lange optie geldt ook voor de korte vorm.)
  -a                     verander alleen de toegangstijd
  -c, --no-create        maak geen nieuwe bestanden
  -d, --date=TEKST       ontleed TEKST en gebruik dat in plaats van de huidige tijd
  -f                     (genegeerd)
  -m                     verander alleen de wijzigingstijd
  -r, --reference=BESTAND gebruik de tijden van dit bestand in plaats van de huidige tijd
  -t STAMP               gebruik [[CC]YY]MMDDhhmm[.ss] in plaats van de huidige tijd
  --time=WORD            zet de gegeven tijd:
                           WORD is access, atime of use: zelfde als -a
                           WORD is modify of mtime: zelfde als -m
      --help     toon deze helptekst en beëindig programma
      --version  toon versie-informatie en beëindig programma

Merk op dat de -d en -t opties verschillende opmaak van tijd-datum accepteert.

Stuur foutrapportages aan <bug-coreutils@gnu.org>;
meld fouten in de vertaling aan <vertaling@vrijschrift.nl>.
root@HP-Kenny:/etc/samba/private# [COLOR="Red"]touch smbpasswd[/COLOR]
root@HP-Kenny:/etc/samba/private# [COLOR="Red"]chmod [/COLOR]
chmod: ontbrekend argument
Typ 'chmod --help' voor meer informatie.
root@HP-Kenny:/etc/samba/private# [COLOR="Red"]chmod --help[/COLOR]
Gebruik:  chmod [OPTIE]... MODUS[,MODUS]... BESTAND
     of:  chmod [OPTIE]... OCTALE_MODUS BESTAND...
     of:  chmod [OPTIE]... --reference=REFERENTIEBESTAND BESTAND...
De modus van elk gegeven BESTAND veranderen naar de gegeven MODUS,
of naar de modus van REFERENTIEBESTAND.

  -c, --changes            een melding geven voor elk veranderd bestand
      --no-preserve-root   '/' niet speciaal behandelen (standaard)
      --preserve-root      op '/' niet recursief werken
  -f, --silent, --quiet    de meeste foutmeldingen onderdrukken
  -R, --recursive          bestanden en mappen recursief behandelen
      --reference=RFBSTND  modus van RFBSTND gebruiken i.p.v. een MODUS-waarde
  -v, --verbose            een melding geven voor elk gezien bestand
      --help     toon deze helptekst en beëindig programma
      --version  toon versie-informatie en beëindig programma

Iedere MODUS is van de vorm '[ugoa]*([-+=]([rwxXst]*|[ugo]))+'.

Stuur foutrapportages aan <bug-coreutils@gnu.org>;
meld fouten in de vertaling aan <vertaling@vrijschrift.nl>.
root@HP-Kenny:/etc/samba/private# 
[/quote]

Something like this maybe? It's more easy to find your commands in all this text.....

---

### Post by Neural oD on 2009-02-03
well I'm not an expert, but maybe I can point you in the right direction. I use zsh - not bash. Zsh is awesome - once u've used it you won't go back to bash. It's also very configurable with colours and all sorts

---

### Post by lakersforce on 2009-02-03
```
alias
```

---

