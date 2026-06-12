---
title: "How to increase the font size of the top menu bar"
date: 2020-09-27
forum: Desktop Environments
---

### Post by satimis on 2020-09-27
Hi all,

Ubuntu 18.04 Gnome desktop

I expect to increase the font size of the top menu bar.

Can I change it on Gnome-tweaks?  If YES please advise how.

If NO, please advise how to do it.  Thanks

Regards

---

### Post by Dennis N on 2020-09-28
Gnome Tweaks won't do it.
In Ubuntu 18.04, the size of the font in the top bar is set by the gnome-shell theme you are using. Look for the file **gnome-shell.css** in the theme's gnome-shell folder. My theme is Flat-Remix-Dark:

```
dmn@Sydney-VM:/usr/share/themes/Flat-Remix-Dark/gnome-shell$ tree -L 1
.
&#9500;&#9472;&#9472; assets
&#9492;&#9472;&#9472; gnome-shell.css

```

I made the changes below. One or both affected the font size.
 
Look for the section labeled "stage" and in there is a font setting. I changed font-size to 12pt.

```
stage {
  font-family: Cantarell, Sans-Serif;
  font-size: 12pt;
  color: #FFF; }

```


also look for this section, where I changed font-size to 1em.
```

#panel {
  font-feature-settings: "tnum";
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.9);
  border-radius: 6px;
  font-weight: normal;
  font-size: 1em;
  height: 2em;
  color: #FFF;
  background: rgba(56, 60, 74, 0.3);
  background-gradient-direction: none;
  transition-duration: 200ms; }
```

I changed these some time ago, and one setting might only be for the font size in the top bar menus. You will have to experiment and find out. 

Note: These settings may not work in Ubuntu 20.04, even if they exist.

---

### Post by tea for one on 2020-09-28
[COLOR="#0000FF"]Dash to Panel [/COLOR]extension from [https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) has two settings for these font sizes.

Dash to Panel settings > Fine-Tune > Tray Font Size
Dash to Panel settings > Fine-Tune > Left Box Font Size

---

### Post by satimis on 2020-09-29
> **Dennis N said:**
> Gnome Tweaks won't do it.
In Ubuntu 18.04, the size of the font in the top bar is set by the gnome-shell theme you are using. Look for the file **gnome-shell.css** in the theme's gnome-shell folder. My theme is Flat-Remix-Dark:
.....

Hi,

Thanks for your advice.  I expect to increase font size.

$ ls /usr/share/themes/```

Adwaita       Ambiance  Emacs         Radiance
Adwaita-dark  Default   HighContrast  Raleigh
```

I suppose my theme is "Adwaita-dark" ?

/usr/share/gnome-shell/theme/gnome-shell.css```

/* TOP BAR */
#panel {
  background-color: rgba(0, 0, 0, 0.35);
  /* transition from solid to transparent */
  transition-duration: 500ms;
  font-weight: bold;  
  height: 1.86em; } 

```
change height:1.86em to 3.86em without effect.

```

stage {
  font-family: Cantarell, Sans-Serif;
  font-size: 11pt;
  color: #eeeeec; }

```
change font-size to 14pt with no effect

Regards

---

### Post by satimis on 2020-09-29
> **tea for one said:**
> [COLOR="#0000FF"]Dash to Panel [/COLOR]extension from [https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) has two settings for these font sizes.

Dash to Panel settings > Fine-Tune > Tray Font Size
Dash to Panel settings > Fine-Tune > Left Box Font Size
Hi,

Thanks for your advice.

Have installed GNOME Shell integration browser extension

On Firefox menu
I could not find```

Dash to Panel settings 

```
Please advise.  Thanks

Regards

---

### Post by tea for one on 2020-09-29
You won't find Dash to Panel settings in Firefox menu.
Dash to Panel settings are part of the Dash to Panel extension.
Have you successfully installed the extension?

---

### Post by satimis on 2020-09-29
> **tea for one said:**
> You won't find Dash to Panel settings in Firefox menu.
Dash to Panel settings are part of the Dash to Panel extension.
Have you successfully installed the extension?
Hi,

I have installed the extension but there is a warning```

Although GNOME Shell integration extension is running, native host connector is not detected. Refer documentation for instructions about installing connector.

```
What shall I do here.  Thanks

Regards

---

### Post by tea for one on 2020-09-29
Did you install [COLOR="#0000FF"]chrome-gnome-shell[/COLOR]?

```
sudo apt install chrome-gnome-shell
```

---

### Post by satimis on 2020-09-29
> **tea for one said:**
> Did you install [COLOR="#0000FF"]chrome-gnome-shell[/COLOR]?

```
sudo apt install chrome-gnome-shell
```
Yes

$ which chrome-gnome-shell```

/usr/bin/chrome-gnome-shell

```

Do I need to install gnome-shell-extensions?
$ apt policy gnome-shell-extensions```

gnome-shell-extensions:
  Installed: (none)
  Candidate: 3.28.0-2
  Version table:
     3.28.0-2 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe i386 Packages

```

$ gnome-shell --version```

GNOME Shell 3.28.4

```

What will be the next step?  Thanks

Regards

---

### Post by tea for one on 2020-09-29
Three ways to find Dash to Panel settings:-

Navigate to [https://extensions.gnome.org/](https://extensions.gnome.org/) > Installed Extensions.

What do you see?

You can also control all settings including Dash to Panel settings via **right click** in an empty space on the top bar in Ubuntu 20.04

You can also use **gnome-tweaks** to access extensions.

```
sudo apt install gnome-tweaks
```

---

### Post by Dennis N on 2020-09-29
> /usr/share/gnome-shell/theme/gnome-shell.css
You are in the wrong folder for making the changes. Look inside the theme folder, which for you would be:

/usr/share/themes/Adwaita-dark

But, when you do, you find Adwaita-dark doesn't have a gnome-shell theme folder!
```
dmn@Sydney:/usr/share/themes/Adwaita-dark$ ls
gtk-2.0  gtk-3.0  index.theme

```
Therefore, you need to find a theme that includes a gnome-shell theme folder and set it as your Shell theme in Tweaks. Like this one (Obsidian): 
```
dmn@Sydney:/usr/share/themes/Obsidian$ ls
assets    [COLOR="#FF0000"]gnome-shell[/COLOR]  gtk-3.0   index.theme  openbox-3
cinnamon  gtk-2.0      gtk-3.20  metacity-1

```
After doing that, open the **gnome-shell** folder:
```
dmn@Sydney:/usr/share/themes/Obsidian/gnome-shell$ ls
assets  [COLOR="#FF0000"]gnome-shell.css[/COLOR]  gnome-shell-theme.gresource.xml

```
Edit file **gnome-shell.css ** to make the changes. Remember, you also have to set the gnome-shell theme in Tweaks: **Themes > Shell**

If you like, you can keep Adwaita-dark as the **application theme** and use another theme to supply the **Shell theme** in Tweaks.

---

### Post by satimis on 2020-09-29
> **tea for one said:**
> Three ways to find Dash to Panel settings:-

Navigate to [https://extensions.gnome.org/](https://extensions.gnome.org/) > Installed Extensions.

What do you see?
NetSpeed
Ubuntu AppIndicators
Ubuntu Dock

> 
You can also control all settings including Dash to Panel settings via **right click** in an empty space on the top bar in Ubuntu 20.04
I'm running Ubuntu 18.04 Gnome desktop here.  Right-click empty space on top bar, nothing happens.

> 
You can also use **gnome-tweaks** to access extensions.

```
sudo apt install gnome-tweaks
```
gnome-tweaks has been running here for some time.  Before my previous posting I have checked it.  Pls see attached screen-shots.

Thanks

---

### Post by satimis on 2020-09-29
> **Dennis N said:**
> You are in the wrong folder for making the changes. Look inside the theme folder, which for you would be:

/usr/share/themes/Adwaita-dark

But, when you do, you find Adwaita-dark doesn't have a gnome-shell theme folder!
```
dmn@Sydney:/usr/share/themes/Adwaita-dark$ ls
gtk-2.0  gtk-3.0  index.theme

```
Therefore, you need to find a theme that includes a gnome-shell theme folder and set it as your Shell theme in Tweaks. Like this one (Obsidian): 
```
dmn@Sydney:/usr/share/themes/Obsidian$ ls
assets    [COLOR="#FF0000"]gnome-shell[/COLOR]  gtk-3.0   index.theme  openbox-3
cinnamon  gtk-2.0      gtk-3.20  metacity-1

```
After doing that, open the **gnome-shell** folder:
```
dmn@Sydney:/usr/share/themes/Obsidian/gnome-shell$ ls
assets  [COLOR="#FF0000"]gnome-shell.css[/COLOR]  gnome-shell-theme.gresource.xml

```
Edit file **gnome-shell.css ** to make the changes. Remember, you also have to set the gnome-shell theme in Tweaks: **Themes > Shell**

If you like, you can keep Adwaita-dark as the **application theme** and use another theme to supply the **Shell theme** in Tweaks.
Hi Dennis

$ ls /usr/share/themes/```

Adwaita       Ambiance  Emacs         Radiance
Adwaita-dark  Default   HighContrast  Raleigh

```
All themes are here.

$ ls /usr/share/themes/Adwaita/```

gtk-2.0  gtk-3.0  index.theme
```

$ ls /usr/share/themes/Adwaita-dark/```

gtk-2.0  gtk-3.0  index.theme
```

$ ls /usr/share/themes/Ambiance/```

gtk-2.0  gtk-3.0  gtk-3.20  index.theme  metacity-1  unity
```

$ls /usr/share/themes/Default/```

gtk-2.0-key  gtk-3.0
```

Is this the default theme?

$ ls /usr/share/themes/Emacs/```

gtk-2.0-key  gtk-3.0
```

$ ls /usr/share/themes/HighContrast/```

gtk-2.0  gtk-3.0  index.theme
```

$ ls /usr/share/themes/Radiance/```

gtk-2.0  gtk-3.0  gtk-3.20  index.theme  metacity-1 unity
```

$ ls /usr/share/themes/Raleigh/```

gtk-2.0
```

I couldn't find gnome-shell theme folder in any of them.

Regards

---

### Post by tea for one on 2020-09-29
In your post no.7, you said that you have installed [COLOR="#0000FF"]Dash to Panel[/COLOR] extension, yet it looks like you haven't installed it all.

If you had installed it correctly, it would appear in gnome-tweaks.

I suspect that you have not installed Dash to Panel at all?

---

### Post by satimis on 2020-09-29
> **tea for one said:**
> In your post no.7, you said that you have installed [COLOR="#0000FF"]Dash to Panel[/COLOR] extension, yet it looks like you haven't installed it all.

If you had installed it correctly, it would appear in gnome-tweaks.

I suspect that you have not installed Dash to Panel at all?
Yes, but there is a warning

I'll install it again

On
[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/)

The gnome-shell version here is 3.28
Which is the latest Extension Version to download
13 or 39?

Can I install it on repo?

Thanks

Regards

---

### Post by Dennis N on 2020-09-29
> I couldn't find gnome-shell theme folder in any of them.
OK, to go this route, you need to get some themes that offer theming for gnome shell. 
This tutorial offers advice on how to change themes, including gnome-shell themes:
[https://itsfoss.com/install-switch-themes-gnome-shell/](https://itsfoss.com/install-switch-themes-gnome-shell/)
Once installed, you can try to edit the font size.

I have used Zuki-shell, Obsidian and Flat-Remix-Dark which all have a gnome-shell theme. They all work in 18.04 I believe.

I see you are also getting advice on gnome-shell extensions like dash to panel. That may work for you, but I personally don't want launchers on the panel (top or bottom bar) so it's not for me. Your choice.

---

### Post by tea for one on 2020-09-29
> **satimis said:**
> Yes, but there is a warning

I'll install it again

On
[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/)

The gnome-shell version here is 3.28
Which is the latest Extension Version to download
13 or 39?

Can I install it on repo?

Thanks

Regards

I do not know the version of Dash to Panel for Ubuntu 18.04 with gnome-shell 3.28.

You will have to use an internet search to identify compatible versions.

As I mentioned in post no. 3 where you asked about font sizes, Dash to Panel will allow you to choose font sizes.

If you are having difficulty in installing gnome-extensions, I suggest that you start a new thread.

---

### Post by tea for one on 2020-09-29
Please show output of this command in code tags

```
gnome-extensions list
```

Example from my PC

```
edited@edited:~$ gnome-extensions list
dash-to-panel@jderose9.github.com
user-theme@gnome-shell-extensions.gcampax.github.com
drawOnYourScreen@abakkk.framagit.org
workspace-indicator@gnome-shell-extensions.gcampax.github.com
desktop-icons@csoriano
ubuntu-appindicators@ubuntu.com
ubuntu-dock@ubuntu.com

```

---

### Post by Dennis N on 2020-09-29
> The gnome-shell version here is 3.28
Which is the latest Extension Version to download
13 or 39?

A tip on installing extensions in general: you should not use the 'Download' option. Just use the off/on switch in upper right and turn it on. It will detect your Ubuntu version and install the correct version of the extension.

---

### Post by satimis on 2020-09-30
> **tea for one said:**
> Please show output of this command in code tags

```
gnome-extensions list
```
........

$ gnome-extensions list```

N: Unable to locate package gnome-extensions
 has no directories

```

$ apt policy gnome-shell-extensions```

gnome-shell-extensions:
  Installed: 3.28.0-2
  Candidate: 3.28.0-2
  Version table:
 *** 3.28.0-2 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
```

$ apt policy chrome-gnome-shell```

chrome-gnome-shell:
  Installed: 10-1
  Candidate: 10-1
  Version table:
 *** 10-1 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status

```

But still I couldn't find Dash-Panel on gnome-tweaks.  Pls refer to attached screenshots

Regards

---

### Post by satimis on 2020-09-30
> **Dennis N said:**
> A tip on installing extensions in general: you should not use the 'Download' option. Just use the off/on switch in upper right and turn it on. It will detect your Ubuntu version and install the correct version of the extension.
Hi,

Thanks for your advice.  Now I have dash-to-panel installed

Regards

---

### Post by satimis on 2020-09-30
Hi tea for one,

Hi

Now I have dash-to-panel installed and it can be found on Gnome-Tweaks.

Tuning it ON;
Top menu bar disappears
Left vertical bar moves to bottom

$ gnome-extensions list```

gnome-extensions: command not found

```

How to proceed to enlarge font on top menu bar?  Thanks

Regards

---

### Post by satimis on 2020-09-30
Hi all,

Now I can increase the font size on top menu bar.

I solved my problem according to following article;
How to change the font in GNOME's top bar
[https://www.modmy.com/how-change-font-gnomes-top-bar](https://www.modmy.com/how-change-font-gnomes-top-bar)

Anyway lot of thanks for all of you to assist me.

Regards

---

### Post by tea for one on 2020-09-30
> **satimis said:**
> 

$ gnome-extensions list```

gnome-extensions: command not found

```



To avoid misinterpretation, it would be advisable to post the command used and the output in the same code block.
[COLOR="#0000FF"]gnome-extensions list[/COLOR] is different from [COLOR="#B22222"]gnome-extensions[/COLOR].

To access the settings in Dash to Panel (via GUI):-

Open gnome-tweaks > Extensions > Little Gear Wheel to the right of Dash to Panel.
Fine-Tune will change font sizes.

---

### Post by satimis on 2020-09-30
> **tea for one said:**
> 
To access the settings in Dash to Panel (via GUI):-

Open gnome-tweaks > Extensions > Little Gear Wheel to the right of Dash to Panel.
Fine-Tune will change font sizes.
No Fine-Tune setting

Pls see attached screenshot

Tuning ON Dash to Panel, Top menu bar and the vertical left menu bar disappear.

Regards

---

### Post by tea for one on 2020-09-30
Do you not have six tabs at the top of the page in your screenshot?

Position Style Behaviour Action Fine-Tune About

---

### Post by satimis on 2020-09-30
> **tea for one said:**
> Do you not have six tabs at the top of the page in your screenshot?

Position Style Behaviour Action Fine-Tune About
No.  My screenshot shows the whole page of my Dash to Panel

Your Dash to Panel looks completely different to my Dash to Panel

Regards

---

### Post by tea for one on 2020-10-01
Well, we're not making much progress so far.........

In your position, it would appear that something is amiss, therefore, I would completely remove Dash to Panel and then install it again from the extensions website.

Navigate to [https://extensions.gnome.org/](https://extensions.gnome.org/) > Installed extensions > Dash to Panel > Uninstall.

Double check that there are no remnants in ~/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com$.

Remove the [COLOR="#0000FF"]Dash to Panel[/COLOR] folder if it is still there.

Power off the PC completely and have a cup of tea/cold beer or your beverage of choice.

Power on and install the extension again via [https://extensions.gnome.org/](https://extensions.gnome.org/)

Any joy?

---

### Post by satimis on 2020-10-01
Hi tea for one,

Thanks for your continue advice and time spent.

I'll get a spare PC to test it.  I'll come back after the test.

Regards

---

### Post by tea for one on 2020-10-01
You don't really need a spare PC to carry out tests.

For example, you could make a [COLOR="#0000FF"]live usb with persistence[/COLOR], assuming you still have access to your Ubuntu Iso.

Preferably, download Ubuntu 20.04 for an up-to-date test.

Then, install gnome-tweaks, chrome-gnome-shell and Dash to Panel.

---

### Post by satimis on 2020-10-01
> **tea for one said:**
> You don't really need a spare PC to carry out tests.
......

I'm now testing my new Dell 32" 4K display on this daily working PC.  I have spare PCs available.  What I'm in short is time.

Regards

---

### Post by satimis on 2020-10-03
Hi tea for one,

Now I come back to continue the test.  To avoid further confusion I list the steps to be performed as follow;

gnome-tweaks and chrome-gnome-shell have been installed.

$ apt policy gnome-tweaks
gnome-tweaks:
  Installed: 3.34.0-2ubuntu1
  Candidate: 3.34.0-2ubuntu1
  VDash to Panel by jderose9ersion table:
 *** 3.34.0-2ubuntu1 500
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe i386 Packages
        100 /var/lib/dpkg/status
        
        
$ apt policy chrome-gnome-shell
chrome-gnome-shell:
  Installed: 10.1-5
  Candidate: 10.1-5
  Version table:
 *** 10.1-5 500
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        500 [http://hk.archive.ubuntu.com/ubuntu](http://hk.archive.ubuntu.com/ubuntu) focal/universe i386 Packages
        100 /var/lib/dpkg/status
        

Gnome shell version is 3.36.4

$ gnome-shell --version
GNOME Shell 3.36.4
        
Install "Dash to panel" according to following URL suggested by you on #3 above;
Dash to Panel by jderose9
[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/)


Upon your confirmation to above.  I'll proceed.

Thanks

Regards

---

### Post by tea for one on 2020-10-03
> **satimis said:**
> 
gnome-tweaks:
Installed: 3.34.0-2ubuntu1  [COLOR="#0000FF"]mine is also 3.34.0[/COLOR]        

chrome-gnome-shell:
Installed: 10.1-5  [COLOR="#0000FF"]mine is also 10.1-5[/COLOR]

Gnome shell version is 3.36.4 [COLOR="#0000FF"]mine is also 3.36.4[/COLOR]

My Dash-to-Panel is [COLOR="#0000FF"]version 39[/COLOR]
My Ubuntu version is [COLOR="#0000FF"]Ubuntu 20.04.1 LTS[/COLOR]
Kernel is [COLOR="#0000FF"]5.4.0-48[/COLOR]

I'm looking forward to reading about a successful result :)

---

### Post by satimis on 2020-10-03
> **tea for one said:**
> My Dash-to-Panel is [COLOR="#0000FF"]version 39[/COLOR]
My Ubuntu version is [COLOR="#0000FF"]Ubuntu 20.04.1 LTS[/COLOR]
Kernel is [COLOR="#0000FF"]5.4.0-48[/COLOR]

I'm looking forward to reading about a successful resis ult :)
Hi tea,

This time I got Dash-to-Panel works

Ubuntu 20.04.1 LTS
Release:        20.04

Kernel 5.4.0-48-generic

Dash-to-Panel
Version 39

Thanks

I think Dash-to-Panel doesn't work on Ubuntu 18.04

Regards

---

### Post by tea for one on 2020-10-03
Splendid - Did you manage to change the font size to your satisfaction?

---

### Post by satimis on 2020-10-03
> **tea for one said:**
> Splendid - Did you manage to change the font size to your satisfaction?
Yes

Thanks

Regards

---

