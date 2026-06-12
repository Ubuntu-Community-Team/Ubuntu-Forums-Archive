---
title: "MP3 in amaroK"
date: 2006-01-17
forum: General Help
---

### Post by Choad on 2006-01-17
i have enabled every repository in "Adept" but i cant find lame, so i cant change the engine used by amaroK, so i cant play my mp3's

any help?

---

### Post by JuanFerS on 2006-01-17
Install the xine engine, some might disagree but it's good.

---

### Post by niviche on 2006-01-17
mp3 is a restricted format, with some legal issues preventing it from being play-able by default in Kubuntu.

To enable mp3-playback, refer to [this wiki article](https://wiki.ubuntu.com/RestrictedFormats).

Then, as JuanFerS, the xine engine for Amarok works for me better than the Gstreamer one.

---

### Post by iam10ninjas on 2006-01-17
I have a strange problem with amaroK.

I just upgraded to amarok 1.3.7 and when I try to start it, I get this error.
```

iam10ninjas@10ninjas:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/lib/amarok/amarokapp: error while loading shared libraries: /usr/lib/libtag.so.1: invalid ELF header

```

Amy ideas as to what causes this and how to fix it?

---

### Post by Choad on 2006-01-17
[QUOTE=niviche]mp3 is a restricted format, with some legal issues preventing it from being play-able by default in Kubuntu.

To enable mp3-playback, refer to [this wiki article](https://wiki.ubuntu.com/RestrictedFormats).

Then, as JuanFerS, the xine engine for Amarok works for me better than the Gstreamer one.[/QUOTE]
thankyou

---

### Post by mycroft on 2006-01-20
[QUOTE=JuanFerS]Install the xine engine, some might disagree but it's good.[/QUOTE]

Bear in mind that some tinkering is required if you want to play audio CDs using the xine engine.

---

