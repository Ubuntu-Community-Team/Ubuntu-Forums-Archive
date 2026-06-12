---
title: "font-related:  css cursive font family + monaco"
date: 2006-04-24
forum: Desktop Environments
---

### Post by eitan on 2006-04-24
hello,

  i have two questions, both font-related.  any assistance would be
  most appreciated as i have to resolve these issues before the weekend.

  1. css defines five generic font-families.  one of them is cursive.
      no cursive font appears to be designated to match that font
   family.  as a test, i'm using a simple web page that i bring up 
   in either epiphany or firefox.  the text font does not change when
    switching to the cursive font-family.

   anyone know how to resolve this??

here's a test sample html page:
```
<html><head><style>
#testing {
  font-size: 3em;
  font-family: cursive; }
</style></head><body>
<div id="testing">This is a test.</div>
</body></html>

```

  2. i have some keynote presentations that i transferred from an old apple notebook that use apple fonts.  one is monaco.  actually i didn't have any major problems with the translation to openoffice.  i'm not sure if i had the monaco font installed or not.  anyhow, i recently upgraded to dapper (beta) and the fonts no longer match.  a large number of slides now appear with text bleeding beyond their designated borders/edges.  i can definitely tell i don't have monaco installed.  are there mac-like fonts available on linux / for dapper?  this may be more of an openoffice question than an ubuntu question, not sure.  again, any hints/help would be most welcome.

sincerely,
/ eitan

---

### Post by souki on 2006-04-24
you can define an alias for the "cursive" font family :

- if you want this alias system wide, put the alias in /etc/fonts/local.conf
- if you want this alias only for your user, put the alias in ~/.fonts.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
        <alias>
                <family>cursive</family>
                <prefer>
                        <family>Monaco</family>
                </prefer>
        </alias>
</fontconfig>
```

if you have the Monaco.ttf font, copy it to your ~/.fonts/ folder
if you don't have it, google is your friend ;)

---

### Post by eitan on 2006-04-24
thank you for your reply!  consider me a newbie from the perspective of font configuration in linux.  i sincerely thank you.

i find it strange that firefox and the browser makers don't ensure that there's a font mapping for the "cursive" family as defined by the css specification.

maybe it should be a responsibility of the os maker.  if so, then the font alias in fonts.conf should be a patch for ubuntu.

i wonder what settings changed in going from breezy to dapper that the monaco font used to work for me before but not anymore.

---

### Post by souki on 2006-04-25
I agree with you, but dapper is still beta
could you post a bug report ?

[QUOTE=eitan]i find it strange that firefox and the browser makers don't ensure that there's a font mapping for the "cursive" family as defined by the css specification.[/QUOTE]

the "fantasy" generic family is also missing

> maybe it should be a responsibility of the os maker.  if so, then the font alias in fonts.conf should be a patch for ubuntu.

yes, the alias should be defined by fontconfig and firefox should provide a way to specify an alternate mapping

> i wonder what settings changed in going from breezy to dapper that the monaco font used to work for me before but not anymore.

please, could someone test this under breezy :
```
grep -ir cursive /etc/fonts/
```

---

### Post by eitan on 2006-04-25
fwiw:  i recall testing "font-family: cursive" in css files on breezy before and it did not work.  thanks again.  (ps: about to file a bug report).

---

### Post by eitan on 2006-04-25
ok, i posted a bug report:

Bug #41361

[https://launchpad.net/distros/ubuntu/+bug/41361](https://launchpad.net/distros/ubuntu/+bug/41361)

---

