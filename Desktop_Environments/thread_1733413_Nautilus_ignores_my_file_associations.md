---
title: "Nautilus ignores my file associations"
date: 2011-04-19
forum: Desktop Environments
---

### Post by hashcode on 2011-04-19
Hi, I have my default text files (also source codes etc.) associated with gedit (checked with ubuntu tweak). However, nautilus tries it to open with some "notepad" - dunno what it is I don't even have such a program. Files are OK, opening them directly from gedit or vim is fine.

Some weird things:

- nautilus correctly displays gedit icon
- I have dualboot system with windows 7 and notepad command looks like it came from "there"
- when I click on open with -> gedit, file is correctly open. However this option is not remembered by nautilus (even though I checked it as always open with ...)
- nautilus (after clicking on open with) also suggest to use some "iexplore" command, I totally don't have idea where that came from ...

Any suggestions? I really don't feel like using another file manager, but opening text files is pretty elementeray action and should work properly.

Thanks

---

### Post by Copper Bezel on 2011-04-19
> - nautilus (after clicking on open with) also suggest to use some "iexplore" command, I totally don't have idea where that came from ...

Holy crap. What the hell came with your Wine install?!

In any case, Nautilus uses Gnome's file associations; it doesn't store its own. Open your mimetype associations file with gedit by running this:

```
gedit ~/.local/share/applications/mimeapps.list
```

and look for the line beginning "text/plain"; it should look sort of like

```
text/plain=gedit.desktop;
```

---

### Post by mikewhatever on 2011-04-19
Can you post the output of the following command:
```
cat /etc/lsb-release
```

...just curious what version of Ubuntu you are running.

---

### Post by Krytarik on 2011-04-19
Wine meddles pretty hefty with file associations and the "Open With" menu, unless you disable all its apps for mimetypes. So, that part is no surprise at all. See here on how to disable them: [http://ubuntuforums.org/showthread.php?p=10479920#post10479920](http://ubuntuforums.org/showthread.php?p=10479920#post10479920)

Also, please post the entire content of "mimeapps.list" Copper was referring to.

---

### Post by hashcode on 2011-04-20
Thanks for responses. I don't have Wine installation, that's super bonus :D
[B]
Copper Bezel[/B] - gedit is right there, strange.

**Mikewhater** - nothing special there, see for yourself
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

**Krytarik** - here are contents for mimeapps.list

[Added Associations]
application/x-rar=mount-archive.desktop;
text/html=userapp-firefox-5YOTTV.desktop;userapp-firefox-5R2VTV.desktop;google-chrome.desktop;
application/x-chm=evince.desktop;
audio/x-mod=vlc.desktop;
application/xspf+xml=vlc.desktop;
text/x-java=gedit.desktop;
text/plain=gedit.desktop;

[Removed Associations]
text/plain=wine-extension-txt.desktop;

I don't mind reinstalling thing unless is whole distro.
The only thing I messed with I can remember is unity and macbuntu, nothing more.

---

### Post by Krytarik on 2011-04-20
> **hashcode said:**
> I don't have Wine installation, that's super bonus :D

I guess you mean Wubi, right? Wine is a Windows API emulator, and is apparently installed at your system. Please try disabling its mimetype associations by following my post I linked to.

---

### Post by hashcode on 2011-04-20
No, I meant Wine. I have actual Windows operating system (dual boot) and I don't need to run windows apps from my Linux. I've never installed Wine as far as I know. 
Shell doesn't recognise "wine" as any command. The only possibility is that it came with netbook edition (sudo apt-get install unity) but I don't think so. I can't even find it in installed app list using ubuntu software center, it actually gives me option to install it since it isn't instaleld on my linux yet.

When i try "locate wine" it points me to some teamviewer files, that's it.

---

### Post by Krytarik on 2011-04-20
How about the content of "~/.local/share/applications" then?

Also, please check with
```
dpkg -l |grep wine
```if it's really not installed.

And remove the remnant entry from your "mimeapps.list".

Update: As it turned out, TeamViewer brings it's own Wine with it. So, those may also be able to meddle with the file associations.

---

### Post by hashcode on 2011-04-20
Krytarik, here's output

alacarte-made-1.desktop         userapp-firefox-5YOTTV.desktop  wine-extension-jpeg.desktop
alacarte-made-2.desktop         wine-extension-chm.desktop      wine-extension-jpg.desktop
alacarte-made-3.desktop         wine-extension-gif.desktop      wine-extension-png.desktop
alacarte-made.desktop           wine-extension-hlp.desktop      wine-extension-rtf.desktop
defaults.list                   wine-extension-htm.desktop      wine-extension-txt.desktop
mimeapps.list                   wine-extension-html.desktop     wine-extension-wri.desktop
mimeinfo.cache                  wine-extension-ini.desktop      wine-extension-xml.desktop
pidgin.desktop                  wine-extension-jfif.desktop
userapp-firefox-5R2VTV.desktop  wine-extension-jpe.desktop

And 
dpkg -l |grep wineprinted out nothing.

I just got rid of teamviewer but it didn't solve the issue :/

---

### Post by Krytarik on 2011-04-20
Then delete all "wine*.desktop" files in there:
> **hashcode said:**
> 
alacarte-made-1.desktop         userapp-firefox-5YOTTV.desktop  wine-extension-jpeg.desktop
alacarte-made-2.desktop         wine-extension-chm.desktop      wine-extension-jpg.desktop
alacarte-made-3.desktop         wine-extension-gif.desktop      wine-extension-png.desktop
alacarte-made.desktop           wine-extension-hlp.desktop      wine-extension-rtf.desktop
defaults.list                   wine-extension-htm.desktop      wine-extension-txt.desktop
mimeapps.list                   wine-extension-html.desktop     wine-extension-wri.desktop
mimeinfo.cache                  wine-extension-ini.desktop      wine-extension-xml.desktop
pidgin.desktop                  wine-extension-jfif.desktop
userapp-firefox-5R2VTV.desktop  wine-extension-jpe.desktop


---

### Post by hashcode on 2011-04-20
I successfully deleted all files but Nautilus still misbehaves.

At least I can confirm, that weird stuff like "notepad" and "iexplore" disappeard from it's context menu.

---

### Post by Krytarik on 2011-04-20
What specific mimetype is this about?
To check it, right-click at the file and then choose "Properties".

You may try adding it manually to "mimeapps.list".

---

### Post by hashcode on 2011-04-20
It's simply plain text document (text/plain)

I added it there (text/plain=gedit.desktop.;) but no result.

This really seems like case for sherlock. I really appreciate all your advices so far :)

---

### Post by Krytarik on 2011-04-20
And what comes up instead of gedit?

Since it is associated with text/plain by default, you may try removing/replacing "mimeapps.list".

I *am* Sherlock! ;-)

---

### Post by hashcode on 2011-04-20
Nothing comes up ... You can just click on file ... forever.
How should I replace that? Only removing and relogging or?

---

### Post by Krytarik on 2011-04-20
> **hashcode said:**
> 
How should I replace that? Only removing and relogging or?
Yeah, just remove it, or place it somewhere else.
But I just got another idea: Try the same with "~/.local/share/mime/mime.cache".

Then relogin, to be sure.

---

### Post by hashcode on 2011-04-20
The result is ... weird.

- some files are correctly opened with gnome (.list,  .h, .c) that I just downloaded
- some .java files are opened with gedit (that I have never tried before, like my old projects I edit with Eclipse not Gedit)
- some .java files are not opened with gedit  (that I have already tried)
- some .txt files are opened with gedit (that I currently created)
- some .txt files are not opened with gedit (that I have already tried before)
and so on ...

It's like some files "knows" that they have been doomed before ... :o

---

### Post by Krytarik on 2011-04-20
It may play a role that in Linux the file type is determined by its content, not by its extension, like in Windows. Please check the mimetypes of those files that aren't associated correctly.

---

### Post by hashcode on 2011-04-21
It behaves too randomly to inspect. Do you think reinstalling of some applications might help?

---

### Post by Copper Bezel on 2011-04-21
What Krytarik is asking for is the displayed mimetype. If you click on a file in Nautilus and select Properties, it'll display the mimetype recognized, like text/plain or application/shellscript or image/gif and such. If those don't consistently match the extensions, we can get a little closer to solving the problem.

---

### Post by hashcode on 2011-04-21
I get it Copper, but some files with text/plain work well and some (with same mimetype) don't :-/

---

### Post by Krytarik on 2011-04-21
> **hashcode said:**
> Do you think reinstalling of some applications might help?
I wouldn't know which. Honestly, right know I don't know what else we could do.

---

### Post by hashcode on 2011-04-21
I wish I could provide more exact specification .... I'll probably do some clean reinstall to natty anyways, so this puzzle will remain unsolved I guess :(

---

### Post by Mfodhu on 2011-05-30
I think i had the same problem - in my case, anything I tried to open through the unity side-bar in natty would always try to open with the same application. I managed to fix it by removing all xfce4, including the lib files (I think the problem was there). They were somehow forcing the file-assocations in ~/.local/share/applications/mimeapps.list and I reset this file by copying /usr/share/applications/defaults.list over to the mimeapps.list file.

---

### Post by Krytarik on 2011-05-30
> **Mfodhu said:**
> ~/.local/share/applications/mimeapps.list and I reset this file by copying /usr/share/applications/defaults.list over to the mimeapps.list file.
The first mentioned one only includes custom set associations, and those override the default ones. So, if you want to revert to the defaults, you can just delete the entire file.

---

### Post by heytracy on 2012-05-19
> **Krytarik said:**
> The first mentioned one only includes custom set associations, and those override the default ones. So, if you want to revert to the defaults, you can just delete the entire file.

OMG!

I've been trying to fix this for a while~ so tired of having to do a work-around just to open a regular file!

Simply re-naming mimeapps.list (I used mimeappz.list) solved it!

Wow.  Thanks  :)

---

