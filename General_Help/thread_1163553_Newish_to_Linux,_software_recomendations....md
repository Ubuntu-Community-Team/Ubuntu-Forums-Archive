---
title: "Newish to Linux, software recomendations..."
date: 2009-05-18
forum: General Help
---

### Post by Nugar on 2009-05-18
Hi all,

I hope this is the appropriate forum for this question.

I have recently switched to Ubuntu Linux, migrating from MS. I didn't change earlier because I need my Photoshop to edit my photographs.

But recently I finally got it to work under Ubuntu, as well as a couple of other programas that I really need.

But there are couple that even though they work using Wine, I'd like to know if a native equivalent exists, and that's the point of this post: asking for your help in suggesting replacements.

For instance, I use for general note-taking a software called MyInfo ( [http://www.milenix.com/myinfo.php](http://www.milenix.com/myinfo.php) ). Is there an equivalent Linux-native software that I can use for that?

Also, I have a rather large collection of CDs and DVDs with every kind of files, from old Word files, to images. And I catalog them using Supercat ( [http://no-nonsense-software.com/supercat/](http://no-nonsense-software.com/supercat/) ). Any suggestions for this functionality?

My favorite text editor is Ultraedit ( [http://www.ultraedit.com/](http://www.ultraedit.com/) ). Any replacements with the same functionality? (goes beyond a simple text editor). It does run fine under Wine, btw, same as Supercat and MyInfo, but I'd prefer going native.

Thanks in advance for any pointers,

Nugar (a.k.a Humberto Olarte Cupas)

---

### Post by C-- on 2009-05-18
> **Nugar said:**
> Hi all,

I hope this is the appropriate forum for this question.

I have recently switched to Ubuntu Linux, migrating from MS. I didn't change earlier because I need my Photoshop to edit my photographs.

But recently I finally got it to work under Ubuntu, as well as a couple of other programas that I really need.

But there are couple that even though they work using Wine, I'd like to know if a native equivalent exists, and that's the point of this post: asking for your help in suggesting replacements.

For instance, I use for general note-taking a software called MyInfo ( [http://www.milenix.com/myinfo.php](http://www.milenix.com/myinfo.php) ). Is there an equivalent Linux-native software that I can use for that?

Also, I have a rather large collection of CDs and DVDs with every kind of files, from old Word files, to images. And I catalog them using Supercat ( [http://no-nonsense-software.com/supercat/](http://no-nonsense-software.com/supercat/) ). Any suggestions for this functionality?

My favorite text editor is Ultraedit ( [http://www.ultraedit.com/](http://www.ultraedit.com/) ). Any replacements with the same functionality? (goes beyond a simple text editor). It does run fine under Wine, btw, same as Supercat and MyInfo, but I'd prefer going native.

Thanks in advance for any pointers,

Nugar (a.k.a Humberto Olarte Cupas)

Gedit (has plugins too) or OpenOffice.org for your documents. A superb Photoshop replacement is the Gimp. These are usually installed by default.
Search under Applications->Add/Remove for more software.

---

### Post by Nugar on 2009-05-19
Hi C--

Thanks for your answer!

Cheers,

Humberto

---

### Post by geraldvillorente on 2009-05-19
Photoshop = GIMP
Dreamweaver = gedit, bluefish, quanta, more.....
Office2003 = OpenOffice
Maya & 3DMax = Blender, Mind's eye, Pixon-anitroll
Messenger = Pidgin
PDF reader = xpdf-viewr
antivirus = no need!!!!

---

### Post by lisati on 2009-05-19
Have a look here: [https://help.ubuntu.com/9.04/switching/applications-equivalents.html](https://help.ubuntu.com/9.04/switching/applications-equivalents.html)

---

### Post by Dex73 on 2009-05-20
As long as you like to view your audio files by artist then by album Decibel Audio Player works great. Allows you to directly access files as you have them stored.(usually by artist then album)

---

### Post by geraldvillorente on 2009-05-20
> **Dex73 said:**
> As long as you like to view your audio files by artist then by album Decibel Audio Player works great. Allows you to directly access files as you have them stored.(usually by artist then album)

Amarok is also good...to install 
```

sudo apt-get install amarok

```

---

### Post by Soul-Sing on 2009-05-20
appfinder for linux: [http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

---

### Post by Nugar on 2009-05-20
Thanks all for your answers. I'll read more on this.

Cheers,

Humberto

---

### Post by colau on 2009-05-20
For multimedia player.
```

aptitude install w32codecs libdvdcss2
aptitude install smplayer

```

---

### Post by krendar on 2009-05-20
There are lots of editors on Linux/Unix. It depends on what you do with your text-editor. If you are programming I think its well worth investing your time in learning vi or Emacs (both has a learning curve, but well worth time invested). If its not programming gedit might very well be all you need (found in the menu Applications | Accessories | Text Editor).

---

### Post by Soul-Sing on 2009-05-20
> **colau said:**
> For multimedia player.
```

aptitude install w32codecs libdvdcss2
aptitude install smplayer

```

The "gstreamer family" does most of the job, w32codecs libdvdcss2
are illegal in some countries.

---

