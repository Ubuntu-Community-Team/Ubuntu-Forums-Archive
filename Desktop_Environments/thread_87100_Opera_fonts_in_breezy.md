---
title: "Opera fonts in breezy"
date: 2005-11-07
forum: Desktop Environments
---

### Post by ivanhelguera on 2005-11-07
Hello everyone, 
I have trouble viewing some webpages in Opera. Fonts are often too small: like in the [http://www.soccer-spain.com]("http://www.soccer-spain.com")
I can work it around by setting the minimal font size to, say, 12. But it messes up viewig pages that  use a small fonts for less important stuff - they are shown at 12, which is (or seems to be) the same size as the main text. 
My system DPI settings are 100 dpi (a 15.4" widescreen LCD at 1280x800). I tried to set the opera6.ini option force DPI = 100, but it did not change the way the ugly font looks. Even setting the DPI to 300 did not move the thing a bit. It *did* change the way many other fonts look: so for example, on the main Ubuntu forums page [http://www.ubuntuforums.org/]("http://www.ubuntuforums.org/") the main "Kubuntu 5.10 Support (KDE)" is sensible to DPI, while the smaller font below ("Support for the Kubuntu Breezy Badger 5.10 Release. Please make sure to post your question in the correct section.") is not. 
Best, IH

---

### Post by Xian on 2005-11-07
1. Use Times New Roman, Tahoma, or Bitstream in Opera for your webpage font.
2. Add this entry in "[User Prefs]" in your ~/.opera/opera6.ini file.

Enable Core X Fonts=0

3. Set up a good /home/~/.fonts.conf similar to this:

```
<?xml version="1.0"?>
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
 <!-- ~/.fonts.conf file to configure user font preferences -->

<fontconfig> 
 
 <!-- Enable sub-pixel rendering -->

 <!--
         <match target="font">
                 <test qual="all" name="rgba">
                         <const>unknown</const>
                 </test>
                 <edit name="rgba" mode="assign"><const>rgb</const></edit>
         </match>
 -->

  
 <!-- Use the Autohinter -->

<match target="font">
        <edit name="autohint" mode="assign"><bool>true</bool></edit>
        </match>

 <!-- Disable Autohinting for bold fonts -->

<match target="font">
    <test name="weight" compare="more">
<const>medium</const>
</test>
    <edit name="autohint" mode="assign"><bool>false</bool></edit>
</match>
  
 <!-- Exclude/Include a range of fonts for Anti Aliasing -->
 
 <!--

 <match target="font">
 <test qual="any" name="size" compare="more">
                 <double>9</double>
         </test>
         <test qual="any" name="size" compare="less">
                 <double>14</double>
         </test>
         <edit name="antialias" mode="assign">
                 <bool>false</bool>
         </edit>
 </match> 

 -->

 </fontconfig>
```

4. Be sure and rebuild the cache of your local fonts:

```
$ sudo fc-cache -f -v
```

5. Check to make sure all your /usr/share/fonts contents are pathed correctly in the xorg.conf file.

---

### Post by ivanhelguera on 2005-11-08
Thank you!
Problem still not solved... Here's what I did: 

> 1. Use Times New Roman, Tahoma, or Bitstream in Opera for your webpage font. 

OK. Webpage normal text is set to Times NR [monotype]

> 2. Add this entry in "[User Prefs]" in your ~/.opera/opera6.ini file.

Enable Core X Fonts=0


Added. 

>  3. Set up a good /home/~/.fonts.conf similar to this: 

I copied/pasted your example. 


>   4. Be sure and rebuild the cache of your local fonts:

```
$ sudo fc-cache -f -v
```


Done 

>  5. Check to make sure all your /usr/share/fonts contents are pathed correctly in the xorg.conf file.

I am not sure what is it supposed to mean. The relevant part of the file is: 
```

Section "Files"
        # paths to defoma fonts
    FontPath 	"/usr/share/X11/fonts/misc"
    FontPath 	"/usr/share/X11/fonts/100dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/75dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    FontPath 	"/usr/local/share/fonts"
EndSection
```

The "/usr/local/share/fonts" include many subdirectories, which are not reffered to there. Is this OK?
Thanks once again, 
IH

---

### Post by stevetone on 2005-11-08
Instead of messing with all the font settings, why not just hit the "+" key on the numeric keypad to temporarily resize the fonts one size bigger ("zoom")? When you no longer need the larger size, use the "-" key on the numeric keypad to reduce the size, or hit "*" on the numeric keypad to return to normal size.

---

### Post by Xian on 2005-11-08
[QUOTE=ivanhelguera]The "/usr/local/share/fonts" include many subdirectories, which are not reffered to there. Is this OK?
[/QUOTE]
Yeah, you don't have to include all the subdirectories. I use Tahoma for my browser font so perhaps that is something you could try and see if it assists with your issue. Below is my font section from xorg.conf. I've added a number of fonts so the list is somewhat more exhaustive.

The webpage you listed looks fine on my box with these settings.


```
Section "Files"
	FontPath	"/usr/share/fonts/misc"
	FontPath	"/usr/share/fonts/cyrillic"
	FontPath	"/usr/share/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/Type1"
	FontPath	"/usr/share/fonts/CID"
        FontPath	"/usr/share/fonts/corefonts"
	FontPath	"/usr/share/fonts/freefont"
	FontPath	"/usr/share/fonts/unifont"
	FontPath	"/usr/share/fonts/default"
	FontPath	"/usr/share/fonts/TTF"
        FontPath        "/usr/share/sharefonts"
        FontPath        "/usr/share/fonts/truetype/msttcorefonts"
        FontPath        "/usr/share/fonts/truetype"
	FontPath	"/usr/share/fonts/ttf-bitstream-vera"
        FontPath        "/usr/share/fonts/terminus"
	FontPath	"/usr/share/fonts/100dpi"
	FontPath	"/usr/share/fonts/75dpi"
	FontPath	"/usr/share/fonts/artwiz"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
```

---

### Post by ivanhelguera on 2005-11-08
[QUOTE=stevetone]Instead of messing with all the font settings, why not just hit the "+" key on the numeric keypad to temporarily resize the fonts one size bigger ("zoom")? When you no longer need the larger size, use the "-" key on the numeric keypad to reduce the size, or hit "*" on the numeric keypad to return to normal size.[/QUOTE]

It's a sort of a solution, yes. 
I would like to understand, however, why these pages do not look the way they do in Win, even if I have all the fonts. 
Best, 
IH

---

### Post by Miguel on 2005-11-08
Just a shoot in the darkness:

Have you installed MS ttf core fonts? These are available in one of the extra repositories (multiverse?? restricted??). If you haven't, try

```

$ sudo apt-get install msttcorefonts

```

It will ask you to install another package (needed to extract .cab's). Just accept and see if there is any luck. 

Hope it helps,

Miguel

PS: It was funny to read "Barcelona keep the pressure on leaders Osasuna". And yes, my team is Osasuna (I am from Pampelune)

---

### Post by ivanhelguera on 2005-11-08
[QUOTE=Miguel]

Have you installed MS ttf core fonts? [/QUOTE]

Yes I did. 

> PS: It was funny to read "Barcelona keep the pressure on leaders 
Osasuna". And yes, my team is Osasuna (I am from Pampelune)

BTW it's a nice site. Good luck!
Best, 
IH

---

### Post by ivanhelguera on 2005-11-08
[QUOTE=Xian]Yeah, you don't have to include all the subdirectories. I use Tahoma for my browser font so perhaps that is something you could try and see if it assists with your issue. Below is my font section from xorg.conf. I've added a number of fonts so the list is somewhat more exhaustive [/QUOTE]

I don't understand quite well - so you have  sudirs listed? My list is much shorter. 
looking at the webpage code, I understood that the troublesome font is MS Sans Serif (I am no HTML coder, so I may be wrong). 
> 

The webpage you listed looks fine on my box with these settings.


I implemented much of what you suggested. The fonts look much nicer (though dicedely non - sans serif...) - it looks like it's TNR, which is standard for wpage content. However, the font is still small. 
The  [ScrSPAINopera.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3437&stc=1&d=1131466065") includes the opera screenshot, the [ScrSpnFRFX.png]("http://www.ubuntuforums.org/attachment.php?attachmentid=3439&stc=1&d=1131466065") is the Firfox one. 


By the way - eliminating the antialiasing part of your config resulted in particualry ugly fonts, so i commented it out. 
Best and thanks, 
IH

---

### Post by shinygerbil on 2005-11-08
If you want to temporarily zoom in on a page, hold Control and scroll the mouse (--slowly ;) )

Steve

---

### Post by ivanhelguera on 2005-11-08
OK! I switched the font to Tahoma as you suggested, and it's OK now!
Thank you!
IH

---

### Post by Xian on 2005-11-08
Glad you got things straight. I figured Tahoma would help.
MSoft does put out great fonts (dang it). :)

---

