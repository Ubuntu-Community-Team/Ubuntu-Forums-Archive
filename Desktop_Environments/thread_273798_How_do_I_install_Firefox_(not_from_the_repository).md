---
title: "How do I install Firefox (not from the repository)"
date: 2006-10-08
forum: Desktop Environments
---

### Post by Athanasius on 2006-10-08
I have been using the latest version of firefox and I really like it but I don't know how to install it like the repo version.  I want to delete the repo version and only use the one downloaded from Mozilla.  How/where do I install it and how to I get links in the menu (like under INTERNET)?

I want to use the 2.0RC2 version

---

### Post by Neobuntu on 2006-10-08
Only the normal Ubuntu prepared Firefox automatically upgrades with the desktop upgrade icon process and regular updates. Most people probably want to stick with that, so they don't forget to update inside Firefox; seperately.

Yet, what's cool? Installing Swiftfox. It is Firefox optimised for your processor, and may be a tad faster. Plus it coexists with the Ubuntu Firefox and manages your plugins automatically between them. One can go back and forth, with only a brief pause; when returning one to the other.

You can simply install Swiftfox (and much more) with Automatix; by checking a check box. If you have not installed Automatix, please see the Automatix web site for **EXACT** intructions for your OS. **K**ubuntu **Dapper** for example.
```
http://www.getautomatix.com/
```
Don't forget to update Swiftfox regularly. Do it from the "Help" menu in Swiftfox. This is greyed out in Ubuntu's Firefox; because Ubuntu's Firefox is updated with all Ubuntu packages.


Anyway, these are my suggestions; to keep it simple.

---

### Post by bruenig on 2006-10-08
I am assuming you are putting it in the /opt directory as that is its purpose. Once you get it in there some symbolic linking would be the easiest way to do it. First link the firefox link to your new firefox wrapper script. Becuase all of the menu stuff and any system stuff uses this symbolic link, everything will be redirected to 2.0 instead of the repo thing you have.
```
sudo rm /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```
Then link the plugins over.
```
sudo ln -s /usr/lib/firefox/plugins/* /opt/firefox/plugins/
```

Nearly everything else as far as settings and stuff are concerned are in your ~/.mozilla directory and so that will work the same regardless of the version you use.

Edit: Anything else you want to keep from your other firefox just link over in the same manner. For instance the searchplugins would be.
```
sudo ln -s /usr/lib/firefox/searchplugins/* /opt/firefox/searchplugins/
```

---

### Post by jackkerouac on 2006-10-08
Under Help, select Check for Updates. If that is greyed out for you, it means you don't have the proper permissions to write to the firefox folder. Close Firefox, and open a terminal. Type:

```
gksudo firefox
```

... and then use Help -> Check for Updates.

---

### Post by Neobuntu on 2006-10-08
Did you test that? ```
**kdesu firefox**
``` is still greyed out for me. I'm thinking this is because it updates with ubuntu auto packaging instead.

---

### Post by Athanasius on 2006-10-08
Thank you, bruenig, it worked wonderfully!  I don't know what all that stuff means but it worked.

The gksudo firefox thing didn't work for me either.

I am not liking all this talk of Debian and Ubuntu dumping the Firefox browser.  When the time comes that there is a separation I want to be sure that I am able to use Firefox :-P

---

### Post by Neobuntu on 2006-10-09
Oh yeah, what? Dump Firefox. Firefoxes Mozilla and Debian/Ubuntu better get it together. Dumping Firefox would be ultimately stupid.

I'll have to look into the details though.

---

### Post by ruffneck on 2006-10-09
Perfect instructions bruenig. Thanks much!

---

### Post by bruenig on 2006-10-09
Probably should mention this, this obviously does not uninstall the other firefox, it is a good thing that it doesn't because you need to use the other firefox's plugins and stuff and it is just easier this way. However when the other firefox updates, it replaces the symbolic link meaning that you are going to need to redo that first command to make sure it gets repointed to your /opt/firefox.
```
sudo rm /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```
This probably is not a long term thing you are going to do, eventually 2.0 will probably be available in the repos and so you won't have to redo the sym link then, but until then, any other updates will mess this setup up, redo that first command to fix it.

---

### Post by beerfan on 2006-10-09
Just extract the tar into ~/bin and run it from there. There is no installation needed and you'll never need to worry about root privileges to get the updates.

---

### Post by bruenig on 2006-10-09
> **beerfan said:**
> Just extract the tar into ~/bin and run it from there. There is no installation needed and you'll never need to worry about root privileges to get the updates.
The point was to make it run from the menus and to have it be used by the system like 1.5 is currently used. You are going to need to do some symlinking for that. It can probably be done in another way but that takes much more effort than just changing the symlink.

---

### Post by beerfan on 2006-10-09
> **bruenig said:**
> The point was to make it run from the menus and to have it be used by the system like 1.5 is currently used. You are going to need to do some symlinking for that. It can probably be done in another way but that takes much more effort than just changing the symlink.

If you want it to run from the menu, then make a menu for it. You can't replace the system Ubuntu Firefox though because it has dependencies (help and other stuff) so there's no point trying.

I currently have 3 versions of Firefox on my system. Ubuntu Firefox, Mozilla Firefox 1.5.x installed to replace the system Firefox with symlinks and et cetera, and Mozilla Firefox 2.0rc2 installed in my home directory. Installing in your home directory is by far the easiest and safest route because I don't need to worry about breaking the silly Ubuntu Firefox mess and upgrading Firefox is trivial because root isn't needed.

You're welcome to differ though.

---

### Post by bruenig on 2006-10-09
> **beerfan said:**
> If you want it to run from the menu, then make a menu for it. You can't replace the system Ubuntu Firefox though because it has dependencies (help and other stuff) so there's no point trying.

I currently have 3 versions of Firefox on my system. Ubuntu Firefox, Mozilla Firefox 1.5.x installed to replace the system Firefox with symlinks and et cetera, and Mozilla Firefox 2.0rc2 installed in my home directory. Installing in your home directory is by far the easiest and safest route because I don't need to worry about breaking the silly Ubuntu Firefox mess and upgrading Firefox is trivial because root isn't needed.

You're welcome to differ though.

Well again, I note that there are different ways. Creating a new menu entry with another command that launched the 2.0 firefox would work as well, although the system would still use the other firefox like when you clicked on html documents on the desktop or in other instances. In fact if you want to take it really to the extreme, you could write a script that enabled you to use different .mozilla directories and have each firefox setup differently. How cool would that be. But the simplest way would be to just change the /usr/bin/firefox symlink to wherever you have 2.0 and then be done with it. It keeps the ubuntu firefox like you said and if you only intend to use 2.0 and can't be bothered to do all the other mess, one simple command is far easier than setting up another menu entry and far faster. (Not to mention that it enables the rest of gnome to use the firefox instead of the ubuntu firefox)

---

### Post by beerfan on 2006-10-10
> **bruenig said:**
> Creating a new menu entry with another command that launched the 2.0 firefox would work as well, although the system would still use the other firefox like when you clicked on html documents on the desktop or in other instances.

Actually, that would only happen if Firefox is not already running. I don't know about you but Firefox is the first program I start up after logging in and it's always running. For good or bad, it's not easily possible to get 2 different versions of Firefox to run at the same time.

> **bruenig said:**
> In fact if you want to take it really to the extreme, you could write a script that enabled you to use different .mozilla directories and have each firefox setup differently. How cool would that be.

Why? You can already have multiple Firefox profiles. Just change your menu to "firefox -profilemanager" and you'll be prompted for the profile you want to run.

---

### Post by bruenig on 2006-10-10
> **beerfan said:**
> Actually, that would only happen if Firefox is not already running. I don't know about you but Firefox is the first program I start up after logging in and it's always running. For good or bad, it's not easily possible to get 2 different versions of Firefox to run at the same time.
I certainly do not run firefox all the time. I run it when I use it, close it when I do not. But perhaps that is a different way we use our OS. I keep mine running constantly even when I am not home. The mere fact that you mention logging in makes me think that perhaps you don't or you turn the computer on and off often.

---

### Post by dmacdonald111 on 2007-12-17
> **beerfan said:**
> Actually, that would only happen if Firefox is not already running. I don't know about you but Firefox is the first program I start up after logging in and it's always running. For good or bad, it's not easily possible to get 2 different versions of Firefox to run at the same time.



Why? You can already have multiple Firefox profiles. Just change your menu to "firefox -profilemanager" and you'll be prompted for the profile you want to run.

Profiles are all very well and good, but it would be nice to have different firefox windows open and each one has different settings. Example: one window would have video and sound, the other wouldn't load java or flash, etc.

---

### Post by beerfan on 2007-12-18
> **dmacdonald111 said:**
> Profiles are all very well and good, but it would be nice to have different firefox windows open and each one has different settings. Example: one window would have video and sound, the other wouldn't load java or flash, etc.

I have determined how to do this since my last post. Just create a launcher for each separate profile that you want to use. For the launcher command use "firefox -a f<n> -P <profile>" where N is a different number and profile is the name of the profile. This lauches separate profiles or even separate versions of firefox for me. I have Ubuntu firefox and various Mozilla firefox nightlies and they all run side by side.

---

