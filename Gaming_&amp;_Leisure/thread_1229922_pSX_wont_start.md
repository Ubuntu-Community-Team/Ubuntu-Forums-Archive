---
title: "pSX wont start"
date: 2009-08-02
forum: Gaming &amp; Leisure
---

### Post by volatilesquirrel on 2009-08-02
I've looked through many tutorials and guides for installing pSX but still can't get it to work.

I've installed v1.13 from the website, I have the proper bios in the bios directory and when I double click the file, receive the bio notice error, select the bios in the file select screen and click OK .... nada.

Anyone know what I'm missing here?

Thanks

---

### Post by Grishka on 2009-08-02
run it from the terminal, and post the errors. :)

---

### Post by ShadowTek on 2009-08-02
I have to sudo killall pulseaudio before I can get it to run.

Also, there is a particular library that needs to be installed if you are running 64bit.

---

### Post by volatilesquirrel on 2009-08-02
this is what i type in to run it and it says there's so such file:

thomas@thomas-laptop:~$ cd /home/thomas/pSX./pSX
bash: cd: /home/thomas/pSX./pSX: No such file or directory

one of the guides said to run it like that, not sure if that's correct.

what's the library i need to run 64 bits?  typing into the terminal "killall pulseaudio" didn't help.

---

### Post by Grishka on 2009-08-02
> **volatilesquirrel said:**
> this is what i type in to run it and it says there's so such file:

thomas@thomas-laptop:~$ cd /home/thomas/pSX./pSX
bash: cd: /home/thomas/pSX./pSX: No such file or directory

one of the guides said to run it like that, not sure if that's correct.

what's the library i need to run 64 bits?  typing into the terminal "killall pulseaudio" didn't help.

you're mangling two separate commands.

```

cd /home/thomas/pSX
``` or ```
cd ~/pSX
``` should put you in pSX directory in your home space. then do
```
./pSX
```
mind the dot. :)

or simply drag the pSX executable into your terminal and press enter. this'll run it as well.

---

### Post by volatilesquirrel on 2009-08-02
ahhh, well this is what it replied:

thomas@thomas-laptop:~$ '/home/thomas/pSX/pSX' 

(pSX:13549): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:13549): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:13549): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:13549): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:13549): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:13549): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:13549): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:13549): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault



i'm guess i'm missing a library?

---

### Post by Grishka on 2009-08-02
no. this is a long-standing issue with pulseaudio. try following the steps I've posted in [this thread](http://ubuntuforums.org/showthread.php?t=1146830) in post #8.

---

### Post by volatilesquirrel on 2009-08-02
I managed to change the soundcard to my device but when i got to step four i couldn't find /root/.pSX/psx.ini
in the terminal typing gksudo gedit /root/.pSX/psx.ini doesn't open it nor can i find it doing the search

---

### Post by dfreer on 2009-08-03
It won't be there until you run pSX as the root user at least once (~/.pSX/psx.ini is a file created by the program upon execution, but it also won't create the file if there is a psx.ini in the current directory IIRC).

---

