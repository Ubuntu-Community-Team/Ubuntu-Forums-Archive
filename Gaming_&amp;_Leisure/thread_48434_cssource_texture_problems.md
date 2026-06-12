---
title: "cs:source texture problems"
date: 2005-07-12
forum: Gaming &amp; Leisure
---

### Post by DarkManX4lf on 2005-07-12
when i try to play cs soruce via steam, thru cedega, in dx9 the textures look like this

[[IMG]http://img339.imageshack.us/img339/4406/cssource2ch.jpg[/IMG]](http://www.imageshack.us)


if i try to set it to dx8 its worse...does anyone else have this problem ? how do i fix this?

and my specs are in my sig.

---

### Post by varunus on 2005-07-12
Do you have the proprietary ATI drivers installed?

---

### Post by DarkManX4lf on 2005-07-13
umm ihave the ati drivers installed from the ATI site. its the 8.14.13 drivers

---

### Post by Mr_Smiley on 2005-07-13
Don't know if this helps but take a look [here]("http://steampowered.custhelp.com/cgi-bin/steampowered.cfg/php/enduser/std_adp.php?p_faqid=282&p_created=1101182584&p_sid=yoZ-_nKh&p_lva=&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD0yNzAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MQ**&p_li=&p_topview=1")

---

### Post by DarkManX4lf on 2005-07-15
nah that didnt help, i couldnt run any of the validation stuff from that site, it says steam is not a protocol.

---

### Post by afonic on 2005-07-15
I think that DX9 doesn't work in Cedega well, that's why you have these problems.

If you need to run CS Source stick to Windows for now...

---

### Post by Mr_Smiley on 2005-07-15
[QUOTE=afonic]I think that DX9 doesn't work in Cedega well, that's why you have these problems.

If you need to run CS Source stick to Windows for now...[/QUOTE]

I can run CS Source with Cedega without any texture problems so it is possible.

---

### Post by DarkManX4lf on 2005-07-15
[QUOTE=Mr_Smiley]I can run CS Source with Cedega without any texture problems so it is possible.[/QUOTE]


can you run it in high qual with good fps?
also when i run CS:S after a while it freezes my whole system....how do i fix this?

---

### Post by afonic on 2005-07-16
[QUOTE=Mr_Smiley]I can run CS Source with Cedega without any texture problems so it is possible.[/QUOTE]
 Are you sure you run it in DX9 mode? I doubt it. Check out the video settings page to find out. It auto-selected DX8 in my case and when I forced DX9 missing textures appeared.

I can run it without missing textures too btw but the speed is awful. For example when I get 90fps at 1280x1024 all settings at the max possible in Windows I get like 40fps in Linux in the same resolution with all the settings in the lowest possible.

I am using a Geforce 6600GT. From what I can see from my laptop the case with ATI drivers is even worse (missing textures even in DX8).

---

### Post by DarkManX4lf on 2005-07-16
yea the ati linux drivers needs to be fixed, or made better

---

### Post by Filleokus on 2005-07-16
> **DarkManX4lf]when i try to play cs soruce via steam, thru cedega, in dx9 the textures look like this

[[IMG]http://img339.imageshack.us/img339/4406/cssource2ch.jpg[/IMG]](http://www.imageshack.us)


if i try to set it to dx8 its worse...does anyone else have this problem ? how do i fix this?

and my specs are in my sig.[/QUOTE]
 hi, The first post!

Look in the config file and make a new private settings for CS:s or maybe the HL2 private settings work? I dont know, and whit private settings i mean:

[QUOTE]
 said:**
> 
"ClipSpaceFix" = "N"

;; Medal Of Honor settings
[AppDefaults\\mohaa.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\mohaa.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"
[AppDefaults\\mohaademo.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\mohaademo.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"

[AppDefaults\\moh_spearhead.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\moh_spearhead.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"
[AppDefaults\\moh_spearhead.exe\\Version]
"Windows" = "win2k"
[AppDefaults\\moh_spearhead_demo.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
[AppDefaults\\moh_spearhead_demo.exe\\opengl]
"FixedGLExtensionBuffer" = "Y"


And so on. in you private config you set "PixelShaders" = "N"'

And all this you do in the cedega config file..

Have a nice day

---

### Post by Mr_Smiley on 2005-07-16
[QUOTE=afonic]Are you sure you run it in DX9 mode? I doubt it. Check out the video settings page to find out. It auto-selected DX8 in my case and when I forced DX9 missing textures appeared.

I can run it without missing textures too btw but the speed is awful. For example when I get 90fps at 1280x1024 all settings at the max possible in Windows I get like 40fps in Linux in the same resolution with all the settings in the lowest possible.

I am using a Geforce 6600GT. From what I can see from my laptop the case with ATI drivers is even worse (missing textures even in DX8).[/QUOTE]

No I do not run it in DX9 mode. I get about the same speed as you, its playable but a lot slower than under Windows.

---

### Post by afonic on 2005-07-17
Yes, I agree it's playable but when you play a game very often you want to see it in its best, so I kept a small windows partition for it! :-)

---

