---
title: "Nicest fonts..."
date: 2014-04-06
forum: Desktop Environments
---

### Post by xxx6 on 2014-04-06
Hi

for buntus 14.04 ...

tia!

---

### Post by DogMatix on 2014-04-06
Personal favourite of mine is the Liberation font family, which I generally turn to. It has sans, serif & mono variants and looks slick and are GNU GPL (I think.)

---

### Post by xxx6 on 2014-04-06
> **DogMatix said:**
> Liberation font family, which I generally turn to. It has sans, serif & mono variants and looks slick

how to install it? what bout droid??

tia!

---

### Post by silex89 on 2014-04-06
Thumbs up for ttf-droid-sans. Awesome fonts. Check out as well Artwiz Fonts and Frutiger. There are a couple of fonts in those packages that are marvelous.

Best of Luck! :)

---

### Post by buzzingrobot on 2014-04-07
Fonts are packaged and available in the Ubuntu repos. Search for them with Software Center, Synaptic, etc.

if you install fonts manually, you can place them in /usr/share/fonts and they will be available to any user on the machine.  Or, you can creat a ".fonts" directory in your home folder, place the new fonts there, and they will be available only to you. 

When you install fonts manually, you either need to log in and out, or open a terminal and run "fc-cache -fv" and "sudo fc-cache -fv", to make the system aware of them.

The basic Microsoft fonts -- Arial, Verdana, etc. -- are available in the ubuntu-restricted-extras package (which also installs Flash and a number of codecs) or in the "ttf-mscorefonts-installer" package.

Google font collection ([https://www.google.com/fonts](https://www.google.com/fonts)) is a good source. 

On Unity, I prefer Ubuntu Medium for window titles and interface use, Droid Sans Mono for monospace and terminal use, and stay with the default Sans (which is Deja Vu Sans) for documents.  I also like Opens Sans and Noto Sans. On Gnome, I stay with the defaults, and find Cantarell Bold displays better than most other bolded fonts I've used.

---

### Post by grahammechanical on 2014-04-07
Ubuntu installs Libreoffice by default and Libreoffice comes with fonts that are then available to other applications. I do not think that the Libreoffice developers would use proprietary fonts. Liberation font is part of the default Libreoffice set of default fonts.

Regards.

---

### Post by xxx6 on 2014-04-07
> **buzzingrobot said:**
> 

On Unity, I prefer Ubuntu Medium for window titles and interface use, Droid Sans Mono for monospace and terminal use, and stay with the default Sans (which is Deja Vu Sans) for documents.  I also like Opens Sans and Noto Sans. On Gnome, I stay with the defaults, and find Cantarell Bold displays better than most other bolded fonts I've used

for browsers which do U use?

---

### Post by buzzingrobot on 2014-04-07
> **xxx6 said:**
> for browsers which do U use?

I use Firefox. I change the default of serif to sans, but do not overide a site's font specification in its CSS.

---

### Post by thevypr on 2014-04-07
I used tewi-font for a simple, small, clean font when I was on Arch.

---

### Post by oldos2er on 2014-04-07
I like Terminus font for the terminal, and Ubuntu fonts for other things. ```
sudo apt-get install ttf-ubuntu-font-family xfonts-terminus
```

---

### Post by bcschmerker on 2014-04-10
**+1 for [oldos2er]("http://ubuntuforums.org/member.php?u=338320").**  I'm currently using monospace fonts except for documents on my 12.04.4-LTS installation and plan to continue the practice for 14.04-LTS, as they make for easier reading of, among other data, URL's in all Web browsers on my rig.  I used Ubuntu® Tweak™ (package: **ubuntu-tweak**) to set the Default font to Ubuntu Mono and the Window Title Bar font to Ubuntu Mono Bold; the Document font to Linux Libertine O (package: **fonts-linuxlibertine**); and the Terminal font to Terminus (package: **xfonts-terminus**); no hinting, and subpixel antialiasing (due to the Hewlett-Packard® HP2009m display unit).  In the Synaptic™ Package Manager, I use GNU® Unifont (package: **ttf-unifont**), except Terminus for the XTerm repeater; likewise Terminus in GNOME® Terminal™ Profile Preferences.  For the Content settings in Mozilla® Firefox®, make that Tribun ADF Medium Standard (package: **ttf-adf-tribun**) for Serif, Gillius ADF No. 2 (package: **ttf-adf-gillius**) for Sans-Serif, and Anonymous Pro (package: **ttf-anonymous-pro**) for Monospace.  Alternately, Linux Libertine O for serif, Linux Biolinum O for sans, and Linux Libertine Display O for monospace can be used (package: **fonts-linuxlibertine**).

Be advised that Windows-centric Web pages, often sent using any release of Microsoft® IIS™, may display more accurately with Times New Roman for Serif, Arial for Sans Serif, and Andale Mono for monospace (package: **ttf-mscorefonts-installer**).

---

