---
title: "Ugly arial bold font"
date: 2012-04-06
forum: Desktop Environments
---

### Post by napsy on 2012-04-06
Hello.

I have a font issue. The bold weight of 'arial' gets really ugly and is stretched too much, compared to normal font weight.

Example. The bolder text should't be so stretched.
[IMG]http://i.imgur.com/sX1aB.png[/IMG]

---

### Post by Frogs Hair on 2012-04-06
What version of Ubuntu ? I am running 11.10 and both arial fonts look much better in Libre Office than yours . I have made no adjustments and installed the MS core fonts from the software center .

  	 	 	 	 	 	   [FONT=Arial, sans-serif][SIZE=5]**Arial Bold Font **[/SIZE][/FONT] 
 

    [FONT=Arial, sans-serif][SIZE=5]Arial Normal Font[/SIZE][/FONT]

---

### Post by napsy on 2012-04-16
Running 12.04 with latest updates ... but with one difference: I can't install the core fonts from apt(there's something wrong with my ISP and can't download the fonts from sourceforge) but installed a custom arial .TTF font in my ~/.fonts directory.

---

### Post by Frogs Hair on 2012-04-16
I am now testing 12.04 since my last post and used the installer for the MS core fonts from the software center moments ago. I have not had to download anything from Sourceforge. I have the medibuntu repository installed, so if the installer is not in your software center that may be the reason. I don't know if the installer was there prior to adding the repository .

---

### Post by mcduck on 2012-04-16
> **Frogs Hair said:**
> I am now testing 12.04 since my last post and used the installer for the MS core fonts from the software center moments ago. I have not had to download anything from Sourceforge. I have the medibuntu repository installed, so if the installer is not in your software center that may be the reason. I don't know if the installer was there prior to adding the repository .

The installer itself downloads the fonts from sourceforge, because of the restrictions on the licence under which Microsoft released those fonts, they can't be included in the package itself and instead the package available in the repositories is just a downloader script that downloads and installs the fonts for you.

---

### Post by Frogs Hair on 2012-04-17
> **mcduck said:**
> The installer itself downloads the fonts from sourceforge, because of the restrictions on the licence under which Microsoft released those fonts, they can't be included in the package itself and instead the package available in the repositories is just a downloader script that downloads and installs the fonts for you.

Thanks , I didn't know the fonts were hosted on Source Forge and I know the installer is not the fonts package.

---

### Post by schtufbox on 2012-04-17
Something is definitely wrong there, should look more like this...

---

### Post by napsy on 2012-04-19
So it's not just me but a real bug. Anyone reported yet?

---

### Post by Frogs Hair on 2012-04-19
> **napsy said:**
> So it's not just me but a real bug. Anyone reported yet?

I had no problem in 11.10 and the MS core fonts look great in 12.04 also . Problems related non official packages don't get much attention on Launchpad.

---

### Post by napsy on 2012-04-19
The problem is in the upcoming 12.04 version of Ubuntu.

Frogs Hair: did you dist-upgrade to 12.04 or was it a clean install?

---

### Post by Frogs Hair on 2012-04-19
> **napsy said:**
> The problem is in the upcoming 12.04 version of Ubuntu.

Frogs Hair: did you dist-upgrade to 12.04 or was it a clean install?

I always preform a clean installation .

---

### Post by napsy on 2012-04-20
I tried putting this in my ~/.fonts.conf
> 
<match target="font">
    <test name="weight" compare="more">
        <const>medium</const>
    </test>
    <edit name="autohint" mode="assign">
        <bool>false</bool>
    </edit>
</match>


Should disable auto-hinting for bold fonts which should fix the wide bold fonts problem but it doesn't. Any other suggestions?

---

### Post by Frogs Hair on 2012-04-20
Other than experimenting with the hinting and antialiasing options in advanced settings I have no suggestions. I was thinking there may have been something carried over from the 11.10 .fontconfig that is causing the problem, but I don't know my way around that folder. I don't if it is safe to delete that folder and restart in order to create a new configuration. I have done that in the past with other hidden folders , but not fonts.

---

### Post by napsy on 2012-04-23
Nevermind, I solved the issue by overwriting the font configuration files and the fonts with those from my arch linux installation and now the fonts look as they should. Don't know what went wrong back then. Anyway, thanks for the help.

---

### Post by Frogs Hair on 2012-04-23
Glad its solved . :)

---

