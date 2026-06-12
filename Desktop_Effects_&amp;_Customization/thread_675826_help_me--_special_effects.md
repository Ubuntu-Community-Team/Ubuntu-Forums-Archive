---
title: "help me-- special effects"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by lordbux on 2008-01-23
hi 
i am new to ubuntu 

i installed compiz and all other stuff needed for special effects

[B]but after setting all....when i went to
APPEARANCE PREFERENCES > VISSUAL AFFECT ...... AND SELECTED COSTOME IT SAYS

"DESKTOP SETTINGS COULDN'T BE ENABLED" :confused: [/B]

WHAT SHOULD I DO GUYS
PLS HELP :popcorn:

---

### Post by b0rka7a on 2008-01-23
1) - Turn off your Caps Lock ;)
2) - Are your graphics card drivers installed ?
3) - Try to install ccsm ( sudo apt-get install compizconfig-settings-manager ), and run it from System > Preferences > Advanced Desktop Effects.

---

### Post by Angadude on 2008-01-23
I know I may be sounding stupid, because you say "compiz and all other stuff",
but just in case, have you enabled xserver-xgl?

---

### Post by lordbux on 2008-01-24
[B]thank you frnds

is not still workin.......er how can i install ccsm from wer 

and x g stuff is installed ....frnd

still sam etrouble[/B]
:( :confused: :confused: :KS

---

### Post by Pandemic187 on 2008-01-24
> **lordbux said:**
>  how can i install ccsm from wer
Open a terminal with Applications>Accessories then enter:

sudo apt-get install compizconfig-settings-manager

Since you're new to Ubuntu you may not have a sudo password. I can't remember how to set it though so if you don't, maybe someone else remembers.:lolflag:

---

### Post by lordbux on 2008-01-25
hi frnd
thanks again 
but  .i already ha dinstalled the compix manager

the exat prob is
........once i   [B]RIGHT CLICK ON DEKTOP > CHANGE DESKTOP BAGROUND

AND FROM   APEEARENCE PREFERENCES > VISSUAL EFFECT (TAB) 

WHEN I SELECT ANY OTHER OPTION OTHER THAN [COLOR="Red"] NONE[/COLOR] FOR VISSUAL EFFECT IT SAYS

VISSUAL EFFECTS COULD NOT BE ENABLED[/B]

NO IDEA WER IT WNT WRONG:confused: :confused: :confused: :confused: :confused:
:( :( :(
THANK FRO THE TROPLE BUT STILL GOT THE PROB

---

### Post by Ub1476 on 2008-01-25
Post the output of this:

```
lspci | grep VGA

compiz
```

---

### Post by lordbux on 2008-01-26
yep    

ma video card ...  
out put for    lspci | grep VGA :------= 
-------------------------------
**01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)**


and out put for compiz  is-------
-----------------------------------
[B]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/B] 


SO WHAT DO YOU THINK IS THE MATETR WITH IT...............FRNDS :confused: :confused:

---

### Post by lordbux on 2008-01-31
> **Ub1476 said:**
> Post the output of this:

```
lspci | grep VGA

compiz
```



here it is

yep    

ma video card ...  
out put for    lspci | grep VGA :------= 
-------------------------------
**01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)**


and out put for compiz  is-------
-----------------------------------
[B]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/B] 

pleas help

---

### Post by Fraktyl on 2008-01-31
Did you follow the instructions on this page to get the current drivers for your video card?

[B][https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)




[/B]

---

### Post by lordbux on 2008-01-31
> **Fraktyl said:**
> Did you follow the instructions on this page to get the current drivers for your video card?

[B][https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)




[/B]


i tryed it .............I downloaded a   .RUN file ...dont know how to run it
tryed terminal....................it says comand doesnot exist 
:confused:
:confused:

---

### Post by Fraktyl on 2008-01-31
Open a terminal, cd to the directory you saved it to.

sudo sh [filename]

Until you get the driver installed, you won't be getting compiz running.  Follow the steps on the website I referenced.  If you come to another stopping point, just ask.

---

### Post by lordbux on 2008-02-01
> **Fraktyl said:**
> Did you follow the instructions on this page to get the current drivers for your video card?

[B][https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)




[/B]
yep......but  i think am not smart enough 
AM NOT GETTING THE EXAT DRIVERE FOR THE CARD

CAN ANYONE GIVE A  DOWNLOAD LING FOR THIS GRAPHICS CARD
[B]
 VIA Technologies, Inc. UniChrome Pro IGP (rev 01)[/B]

pls hep guys
:confused:      :lolflag:

---

