---
title: "j2re plugin and firefox"
date: 2006-03-31
forum: Desktop Environments
---

### Post by GiantsFanMan11 on 2006-03-31
Greetings,
I have been trying to get the j2re plugin to work in firefox with no success.  The j2re is installed and I have tried to link them like so:

steve@ScubasLappy:/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

I have also tried linking libjavaplugin_oji.so from these other locations with no luck:

/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/j2re1.5-sun/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

any help would be great.  Thanks.
-Steve

---

### Post by xenmax on 2006-03-31
Probably a silly question to ask, but are you sure yau are in the firefox plugins directory when you created the link?

Also, for me, although the how-tos i followed mentioned that creating a link in 
/usr/local...../plugins will enable jre for all users. firefox was not detecting plugin until i placed a link in plugins dir in ~/.mozilla or something like that.

---

### Post by GiantsFanMan11 on 2006-03-31
I am in the following location when trying to create the link:

/usr/lib/mozilla-firefox/plugins

---

### Post by jrib on 2006-03-31
Did you close all instances of firefox and open it again after doing that?

How did you install j2re?

Does /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so actually exist?  What does ```
ls /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
``` say?

---

### Post by GiantsFanMan11 on 2006-04-01
Here are the results of ls and locate:

```
steve@ScubasLappy:~$
ls /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

steve@ScubasLappy:~$ locate libjavaplugin_oji.so
/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
/usr/lib/j2re1.5-sun/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

So it definitely exists.

---

### Post by xenmax on 2006-04-02
Did you try placing this link 
```
libjavaplugin_oji.so -> /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
```
in the ~/.mozilla/plugins directory? For me, firefox only detected jre plugin after i did this.

---

### Post by GiantsFanMan11 on 2006-04-02
[QUOTE=xenmax]Did you try placing this link 
```
libjavaplugin_oji.so -> /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
```
in the ~/.mozilla/plugins directory? For me, firefox only detected jre plugin after i did this.[/QUOTE]

Isn't that what the following code does:
```
steve@ScubasLappy:/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```
Because if its not, then I have been doing this thing totally wrong.

---

### Post by xenmax on 2006-04-02
> Isn't that what the following code does:
     Code:
     [LEFT]steve@ScubasLappy:/usr/lib/mozilla-firefox/plugins$ sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so[/LEFT]
 
 No. It places the link to your library in /usr/lib/mozilla-firefox/plugins directory, assuming that thing in your prompt is the present working directory. Where as i suggested trying placing a link to the library file in ~/.mozilla/plugins which is same as /home/yourusername/.mozilla/plugins directory

To do this, cd to required directory
```
cd ~/.mozilla/plugins
``` and try any one of these
```
ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
``` or since your created this link, you can link to the link itself
```
ln -s /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
```

EDIT: Remember to restart the firefox browser.

---

### Post by GiantsFanMan11 on 2006-04-02
Hey, it worked!!!
Thanks a lot for the tip.

---

### Post by melissathespud on 2006-04-14
I know this is bringing up an old thread, but it was the closest I could find to what I had tried.  I tried (among many other things) this suggestion, and it is still not working.  Any more suggestions?  

Here's what I can remember that I have done.  I downloaded sun java from their site, and installed following their directions.  No success.  I downloaded just about everything I could find related to java from the package manager, no success either.  I followed all of the wiki instructions I could find for making java work, no success.  I tried this, no succes.  Help?

---

### Post by melissathespud on 2006-04-14
Also, java works just fine in epiphany.

---

