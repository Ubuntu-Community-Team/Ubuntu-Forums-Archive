---
title: "Changing font colours in Unity."
date: 2014-10-25
forum: Desktop Environments
---

### Post by Northernen on 2014-10-25
Hello.

I have some struggles with the current colour scheme/font colour schema in Unity. In certain scenarios, the letters are too bright for me to read.

For instance, this is a screen shot from an empty textbox in Firefox:

[IMG]http://imgur.com/6HDTXty[/IMG][IMG]http://i.imgur.com/6HDTXty.png?1[/IMG]

The text is too light a grey for me to be able to read it without squinting. I use glasses, and this is becoming quite a problem, not just in Firefox, but in many applications. I'm sure I can override this somehow in Firefox, but it has to take it from Unity somehow.

How do I change this in Unity?

---

### Post by ajgreeny on 2014-10-25
Have you tried changing the theme?

I don't use unity so I'm not sure how to do that, or even if it's possible, but look around in the settings manager and I expect there will be some options there.

---

### Post by buzzingrobot on 2014-10-25
Font color is an attribute of the theme, where it is typically controlled, in Unity themes, by the theme's CSS.  A easier, more foolproof way to change would be to install a variety of new themes for Unity and see if one is to your tastes.

Also, install "unity-tweak-tool" from the repos, which will allow you to enable new themes once installed, as well as change the font settings, as well as a number of other useful tweaks Systems Settings don't include.

Some themes are in the repos.  The noobslab.com site has a good collection of themes, broken out by Unity version, and instructions on installation. (Essentially, the downloaded archive is extracted and the folder that's created and all the files in it are copied to /usr/share/themes.)

---

### Post by vasa1 on 2014-10-25
It's quite possible that changing themes may not affect how the content of a web page appears. It *may* affect only "chrome"-related aspects.

With that in mind, you may consider the High Contrast theme which is part of "gnome-accessibility-themes - Accessibility themes for the GNOME desktop" in the standard software center. This theme isn't known for its beauty.

I come across web pages with this light grey text on a nearly white background quite often. If it happens on pages I visit regularly, I try to fix the issue using a stylesheet: in the very brief image you've provided, I can't figure out the context but something like ```
.textbox-input, textarea { font-family: monospace !important; font-size: 16px !important; color: #678aaa !important; background: #000010 !important }
```may help.

---

### Post by CantankRus on 2014-10-26
These are a few things I do which help my old eyes.
**1)** Use darker themes. My favourite and one I have used for a couple of years is **MediterraneanNight** available from the noobslab ppa mentioned earlier.
[**_[COLOR="#B22222"]Mediterranean Themes Updated For 14.04[/COLOR]_**]("http://www.noobslab.com/2014/05/mediterranean-themes-updated-for-1404.html")
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install mediterranean-theme
```
The **mediterranean-theme** pack contains numerous themes you can try.


**2) **Adjust your gamma and color temps with **redshift-gtk**. 
Gives you a panel indicator where you can toggle the redshift settings on/off.
This is the config I use @ ~/.config/redshift.conf
```
[redshift]
temp-day=4500
temp-night=3700
gamma=0.85
adjustment-method=vidmode
location-provider=manual

[manual]
lat=-31.95
lon=115.86

[vidmode]
screen=0
```


**3)** Use **gtk-theme-config** to change some colours.
[ATTACH=CONFIG]257497[/ATTACH]

All of these help to eliminate bright whites and ease the eyes.

---

### Post by vasa1 on 2014-10-27
I use```
img { opacity: 0.4 !important; border: none !important }
img:hover { opacity: 1 !important }

```in my browser's stylesheet to dim images; if I want to see an image in full brightness I bring the mouse pointer over the image.

---

