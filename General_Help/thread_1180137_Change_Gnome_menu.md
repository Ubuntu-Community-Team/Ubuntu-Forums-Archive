---
title: "Change Gnome menu"
date: 2009-06-06
forum: General Help
---

### Post by Veector on 2009-06-06
how can i  change the "aplication" "places" "system" names in the gnome menu

---

### Post by Legace on 2009-06-06
I found this:

I figured out how to change the "Applications", "Places" and "System" titles in the gnome-panel. Basically you have to create a new translation file for those words and put it in en_US. If you aren't using the US local, you can add/change the gnome-panel-*.mo file to whatever you want it to be.

For en_US people here's the steps.

1) Make a new text file on your desktop called **panel** which has the follow text in it:

```
msgid ""
msgstr ""
"Project-Id-Version: gnome-panel trunk\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2008-05-26 00:59+0000\n"
"PO-Revision-Date: 2008-05-26 00:59+0000\n"
"Last-Translator: YOUR NAMR\n"
"Language-Team: None\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Plural-Forms: nplurals=1; plural=0;\n"
"X-Launchpad-Export-Date: 2008-04-16 01:47+0000\n"
"X-Generator: Launchpad (build Unknown)\n"

msgid "Applications"
msgstr "YOUR NAME FOR APPLICATIONS"

msgid "Places"
msgstr "YOUR NAME FOR PLACES"

msgid "System"
msgstr "YOUR NAME FOR SYSTEM"
```


2) Open Applications -> Accessories -> Terminal and type in:
```
sudo apt-get install gettext
```

Once you have it installed, type in:
```
cd ~/Desktop
```


Then type in:
```
msgfmt panel
```

3) Then run
```
sudo mv messages.mo /usr/share/locale-langpack/en_US/LC_MESSAGES/gnome-panel-2.0.mo
```

4) Then run the following and it should work:
```
pkill gnome-panel
```

---

