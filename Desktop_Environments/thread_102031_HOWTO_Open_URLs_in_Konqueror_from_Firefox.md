---
title: "HOWTO: Open URLs in Konqueror from Firefox"
date: 2005-12-11
forum: Desktop Environments
---

### Post by magnusbb on 2005-12-11
[SIZE="4"]**HOWTO: Open URLs in Konqueror from Firefox**[/SIZE]

(This also applies for GNOME users who want the power of Konqueror).

I am using Firefox most of the time, and I think it's an excellent browser. But sometimes Konqueror does a better job on the rendering and therefore I 
wanted the option to open some sites in Konqueror just by right-clicking a site in Firefox.

To accomplish this I installed the "IE View Lite" extension from this page:
[https://addons.mozilla.org/extensions/moreinfo.php?id=1429&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=1429&application=firefox)

But this extension is targeted at Windows users wanting Firefox to open some sites in Internet Explorer. Well, we now want to mod it, to get it to work with Konqueror.

After you have installed it and restarted Firefox, click on your location bar and type **about:config**

Search for **ieview.path** and replace the string with the path to Konqueror: **/usr/bin/konqueror**

A restart of your browser, and sites should now open in Konqueror if you right click them.

------------------------------------------------
**OPTIONAL MOD:**

The last mod is optional, but I recommend it for practical reasons. That is to change the text "View This Page in IE" with "Konqueror".

Open your local mozilla directory in **/home/user/.mozilla/firefox/** and find your Extensions directory. On my computer this directory was located under a somewhat awkward name: obwl3l21.default. It may be different for you, so do a search for it, if you can't find it. 

Inside this directory find the directory called **{FDD8ECF0-451A-414D-8C8F-7B7F78B0ECD3}**,  open it and go through **chrome -> content** and find the file called **ieviewOverlay.xul** and open it in a text editor. Their you will find the line to change, simply replace the text **IE** with **Konqueror** and save it.

Restart your Firefox and enjoy the power of both browsers! In Konqueror an "Open in Firefox" is already provided in the right-click actions menu.

---

### Post by l.tambiah on 2005-12-11
Useful hack, but this post would be more suited towards the Kubuntu Forum.

---

### Post by magnusbb on 2005-12-11
I know, I've also posted it in the Kubuntu forums. 

I am a Ubuntu "GNOME" user, but I'm also using some KDE apps in GNOME - Konqueror is one of them. Mixing the two environments works good here, especially with the new KDE 3.5 which is a lot faster and more stable than the previous releases.

---

