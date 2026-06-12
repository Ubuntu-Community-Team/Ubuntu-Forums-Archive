---
title: "e17 install, a number of packages 'skipped'. Why?"
date: 2009-02-10
forum: General Help
---

### Post by agim on 2009-02-10
Can anyone tell me why so many packages are being 'skipped' on my e17 install?
I followed these instructions.
[http://ubuntuforums.org/showthread.php?t=916690&highlight=e17+intrepid](http://ubuntuforums.org/showthread.php?t=916690&highlight=e17+intrepid)

Here is some of the output.


- drawer ..................... ok
- efm_nav .................... SKIPPED
- efm_path ................... SKIPPED
- emu ........................ SKIPPED
- execwatch .................. ok
- flame ...................... SKIPPED
- forecasts .................. ok
- iiirk ...................... ok
- language ................... SKIPPED
- mail ....................... ok
- mem ........................ ok
- moon ....................... SKIPPED
- mpdule ..................... SKIPPED
- net ........................ ok
- news ....................... SKIPPED
- notification ............... SKIPPED
- penguins ................... SKIPPED
- photo ...................... SKIPPED
- places ..................... ok
- rain ....................... SKIPPED
- screenshot ................. ok
- slideshow .................. ok

---

### Post by Tux Aubrey on 2009-02-11
Rui's e17_svn script uses a variation on a script called easy_e17.sh.  When e17_svn is run for the first time (or when you use it to update) it calls easy_e17 and downloads the easy_e17 "default" list of svn components to /var/cache/e17_src.  The list of  components actually downloaded on your system is "hard coded" into easy_e17.sh (in /usr/bin) - it reads:

```
packages="eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus exalt e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan"
```

That's the entire svn tree "trunk" as it currently stands.

The script then looks to a configuration file called easy_e17.conf (/etc/easy_e17.conf) which contains the list of packages that will NOT be compiled and installed - the "skip" list.  My easy_e17.conf currently reads:

```
--skip=esmart,enhance,exml,imlib2,edb,edje_player,edje_viewer,emotion,entrance,
eclair,evfs,evolve,elicit,elitaire,emphasis,empower,engycad,entrance_edit_gui,
entropy,ephoto,estickies,expedite,exquisite,extrackt,engage,enthrall,exalt,exhibit,
rage,emu,flame,moon,news,penguins,rain,snow,language,photo,efm_path,efm_nav,
e_phys,mpdule,notification,

```
(By the way, If you have an earlier version of the .conf file with a "conflicts" line above the --skip line, delete that line.)

There are several reasons for "skipping" individual components:

- they may be old, unmaintained and not working anymore;
- they may be new and very unstable;
- they may have been superseded by something better;
- they may be "just" demo eye-candy programs;
- they may be developer tools not generally required by "normal" people.

Rui put the current "skip" list together from his own experience and after consulting other users.  But there is no rule that says you have to accept it!

You can delete packages from the skip list if you'd like to try them (eg. mine (above) has edje_editor deleted - it is more of a developer/designer tool) by editing the file in any text editor and then running "easy_e17.sh --only=packagename1 for each one you delete from the list.

To get edje_editor, for example, I deleted the name "edje_editor, from easy_e17.conf and then ran:

```
sudo easy_e17.sh --only=edje_editor
```

All the installed packages live in /opt/e17 by the way.

If you use easy_e17.sh to update an existing installation, it will also skip package for which there are no updates - ie your version is the current one.

The other thing you will find is that not all the components you do have on board will be enabled by default - look in the Settings>Modules dialog for a list of available and loaded modules.

Good Luck with e17!

---

