---
title: "aspell in Kile not working"
date: 2006-11-02
forum: Desktop Environments
---

### Post by boban on 2006-11-02
Hi!

I have a problem with Kile and aspell under Ubuntu (Edgy)... I have installed dictionary for my language via aptitude (aspell-pl), but when I choose Tools->Spelling I got: "I(A)Spell could not be started.". 

Aspell works when triggered directly from command line (aspell check filename).

---

### Post by boban on 2006-11-08
anybody?

---

### Post by dangerous666 on 2006-12-07
Same here :(

---

### Post by boban on 2006-12-08
> **dangerous666 said:**
> Same here :(

I figured, that without kde it's hard to enforce aspell on kile... But I found that ispell works quite well...

---

### Post by Toufik on 2006-12-11
I found the solution to the problem!

The spellchecker in KDE is managed via KControl.  By default, it uses ispell.  That's why ispell works but not aspell.

Solution: 
1)install kcontrol
```
$ sudo apt-get install kcontrol
```
2)launch it
```
$ kcontrol
```
3)Select KDE Components > Spell Checker
4)Choose aspell as client (and utf-8 as encoding)

Hope it helps

---

### Post by boban on 2006-12-12
Thanks Toufik... It should work now... But I had to drop Ubuntu - with my new motherboard I only managed to install Gentoo... But maybe with Fiesty I'll be back :)

---

### Post by andiii on 2006-12-13
> **Toufik said:**
> I found the solution to the problem!

Solution: 

Thanks a lot, this works for me!

---

### Post by der_vegi on 2007-02-14
but isn't there another solution without installing kcontrol? i've got the same problem using xubuntu edgy.

---

### Post by der_vegi on 2007-02-14
okay, i've installed kcontrol and changed the settings as mentionend above. a ```
grep -i spell -R /home/mm/.kde
``` gives me the following:
```
/home/mm/.kde/share/config/kdeglobals:[KSpell]
/home/mm/.kde/share/config/kdeglobals:KSpell_Client=1
/home/mm/.kde/share/config/kdeglobals:KSpell_DictFromList=1
/home/mm/.kde/share/config/kdeglobals:KSpell_Dictionary=de-neu
/home/mm/.kde/share/config/kdeglobals:KSpell_Encoding=11
/home/mm/.kde/share/config/kdeglobals:KSpell_NoRootAffix=0
/home/mm/.kde/share/config/kdeglobals:KSpell_RunTogether=0

```

so you have to change the file ```
~/.kde/share/config/kdeglobals
```. but i don't know what numbers you have to set for the different languages.

---

### Post by rusyear04 on 2007-05-04
[COLOR="DarkRed"]
:KS  coool... thanx!!! :KS 

posting #6 did work fine for me!
[/COLOR]

---

### Post by cherry316316 on 2007-11-11
> **rusyear04 said:**
> [COLOR="DarkRed"]
:KS  coool... thanx!!! :KS 

posting #6 did work fine for me!
[/COLOR]

how did u make aspell or what ever work in kile
when i tried to go 
settings->configure kile->kile->complete->dictionary
its asking for some complete file .cwl
and when i navigate to aspell folder, thr is no .cwl file  ,
i found .cwl.gz files , and when i selected them, kile
gives me warning , saying "you might have changed the folder'
and then it don't add that .cwl.gz file also.

:((:confused:

---

### Post by IntuitiveNipple on 2007-11-12
Confirming that editing the file  **~/.kde/share/config** and ensuring it includes:
```
[KSpell]
KSpell_Client=1
KSpell_Encoding=11
KSpell_DictFromList=1
KSpell_Dictionary=en
KSpell_NoRootAffix=0
KSpell_RunTogether=0

```
will allow KDE apps installed in Gnome (not using KDE as the Desktop) to use Aspell. This solved the failed-to-find-spell-checker error in Quanta Plus document editor. 

It still hasn't solved how to get the spell-check to ignore the XHTML document's tag spelling!

The values are:
```
enum KSpellClients {
 KS_CLIENT_ISPELL=0,
 KS_CLIENT_ASPELL=1,
 KS_CLIENT_HSPELL=2
};

enum Encoding {
 KS_E_ASCII=0,
 KS_E_LATIN1=1,
 KS_E_LATIN2=2,
 KS_E_LATIN3=3,
 KS_E_LATIN4=4,
 KS_E_LATIN5=5,
 KS_E_LATIN7=6,
 KS_E_LATIN8=7,
 KS_E_LATIN9=8,
 KS_E_LATIN13=9,
 KS_E_LATIN15=10,
 KS_E_UTF8=11,
 KS_E_KOI8R=12,
 KS_E_KOI8U=13,
 KS_E_CP1251=14,
 KS_E_CP1255=15
};

```

---

