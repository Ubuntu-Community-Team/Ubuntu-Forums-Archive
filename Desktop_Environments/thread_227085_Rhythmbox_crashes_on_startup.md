---
title: "Rhythmbox crashes on startup"
date: 2006-08-01
forum: Desktop Environments
---

### Post by padre999 on 2006-08-01
Since a few days Rhythmbox won't start anymore on my computer. When I start it, the gui comes up and then a error message asking me if I want to restart or close the application.

When I start it in the Terminal I get the following:

```
padre@schlepptopp:~$ rhythmbox

(rhythmbox:6742): Rhythmbox-WARNING **: Unable to start mDNS browsing

RhythmDB-ERROR **: file rhythmdb.c: line 2416 (rhythmdb_entry_set_internal): assertion failed: (g_utf8_validate (g_value_get_string (value), -1, NULL))
aborting...

```

Anybody knows how to fix this? I reinstalled Rhythmbox but the problem remains.

Thanks

---

### Post by jordilin on 2006-08-01
I see from synaptic that there are two versions of rhythmbox which are:
rhythmbox
and
rhytmbox-dbg
Which one have you installed? I have installed the first one "rhythmbox" and I don't experience any problem.

---

### Post by fireedo on 2006-08-01
yes same with me rhythmbox is not working anymore

> (rhythmbox:5281): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:5281): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:5281): Rhythmbox-WARNING **: Unable to start mDNS browsing
The program 'rhythmbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3004 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by padre999 on 2006-08-02
> **fireedo said:**
> yes same with me rhythmbox is not working anymore
No offence, but I think this is not the same problem that you have. The result might be the same, i.e. Rythmbox is not working anymore, but the cause is different.

@ jordilin: I have the normal rhythmbox package installed.

It used to work fine for weeks. Just recently it quit.

As far as I understand the error message that I get, there is something wrong in the file rhythmdb.c. But I can not locate this file anywhere!? I guess it is the rhythmbox database that causes the problem?

Any help would be appreciated.

Thanks

---

### Post by jordilin on 2006-08-02
> (rhythmbox:6742): Rhythmbox-WARNING **: Unable to start mDNS browsing
I also get this message, but rhythmbox starts without problems. 
Go to Edit->preferences->Library and see if you have enabled monitorization of your library (or sth like that, as I don't have english in my box). Perhaps, that is causing your problem. To see where rhythmdb.c is, type 
```
locate rhythmdb.c
```
Take into account that I don't have any file called rhythmdb.c in my box. If you have it, move it to your home directory and start rhythmbox again.

---

### Post by rotten777 on 2006-08-02
> **jordilin said:**
> I also get this message, but rhythmbox starts without problems. 
Go to Edit->preferences->Library and see if you have enabled monitorization of your library (or sth like that, as I don't have english in my box). Perhaps, that is causing your problem. To see where rhythmdb.c is, type 
```
locate rhythmdb.c
```
Take into account that I don't have any file called rhythmdb.c in my box. If you have it, move it to your home directory and start rhythmbox again.



I have the same issue. Why whould it crash when one of it's features is enabled? I know for a fact that it's searching my library because I just dumped another 3GB of music in there.

If only Amarok was native to GNOME...

---

### Post by jordilin on 2006-08-02
> **rotten777 said:**
> I have the same issue. Why whould it crash when one of it's features is enabled? I know for a fact that it's searching my library because I just dumped another 3GB of music in there.

If only Amarok was native to GNOME...

You can always use Listen. An amarok like app for Gnome. It is the one I'm using now.
take a look here:
[http://listengnome.free.fr/](http://listengnome.free.fr/)
and here:
[http://www.ubuntuforums.org/showthread.php?t=126080](http://www.ubuntuforums.org/showthread.php?t=126080)

---

### Post by rotten777 on 2006-08-02
> **jordilin said:**
> You can always use Listen. An amarok like app for Gnome. It is the one I'm using now.
take a look here:
[http://listengnome.free.fr/](http://listengnome.free.fr/)
and here:
[http://www.ubuntuforums.org/showthread.php?t=126080](http://www.ubuntuforums.org/showthread.php?t=126080)


Awesome. I tried Banshee and it failed. I completely retagged my 4700+ songs. And still Rhythmbox and Banshee failed.

I tried Listen, it not only works but it works with more features and seems to be more intuitive. Great stuff!

thanks!

---

### Post by RAOF on 2006-08-02
> **jordilin said:**
> I also get this message, but rhythmbox starts without problems. 
Go to Edit->preferences->Library and see if you have enabled monitorization of your library (or sth like that, as I don't have english in my box). Perhaps, that is causing your problem. To see where rhythmdb.c is, type 
```
locate rhythmdb.c
```
Take into account that I don't have any file called rhythmdb.c in my box. If you have it, move it to your home directory and start rhythmbox again.

The file **rhythmdb.c** is where in the RhythmBox **source code** the error is.  It won't be on your system.

But the error seems to be in your database, or at least in reading it.  Perhaps you should regenerate it, and see if that works.  Try
```
mv ~/.gnome2/rhythmbox ~/rhythmbox-backup
```
and then start Rhythmbox again.  I think that's the right directory; it might be some other one inside the ~/.gnome2 directory if it isn't.

---

### Post by heatpumpcontrol on 2007-11-02
My Rhythmbox was crashing (Gutsy clean install) while reading the files off the network and when started off the GUI. I started it using terminal and this time it seems to be going through it all without a glitch so far. I'll report back if it fails. So far so good.

IT WORKED. 

I tried it again using the GUI and this time it worked that way too. :confused: strange. It crashed several times for me using the GUI before....

---

### Post by squirage on 2007-11-07
Hi All,

Ever since upgrading to Gutsy; Rhythmbox, Totem and Mplayer have all stopped working. I have also had a resurgence of a problem with youtube not playing in firefox. This is something that I had fixed by installing pulseaudio and alsa-oss under Feisty.

I ran rhthymbox in the terminal and turned off all plugins and it still hung when I tried to play a song. It does the same thing for radio. I then have to "force quit"

the terminal had this```
rhythmbox 
JACK tmpdir identified as [/dev/shm] 
Killed
```

Next I tried totem to play a video, and get back a blank box which should have an error message. Of course it doesn't play and again I have to "force quit".

The terminal says```
 totem

JACK tmpdir identified as [/dev/shm]

JACK tmpdir identified as [/dev/shm]

** Message: Error: Failed to write data to the esound daemon

esdsink.c(415): gst_esdsink_write (): /play/abin/audiosinkbin/audio-sink/bin6/autoaudiosink1/autoaudiosink1-actual-sink-esd:

system error: Broken pipe



Killed

```

Then for fun I tried mplayer
```
mplayer

MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team

CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)

CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1

Compiled with runtime CPU detection.

Usage:   mplayer [options] [url|path/]filename



Basic options: (complete list in the man page)

 -vo <drv>        select video output driver ('-vo help' for a list)

 -ao <drv>        select audio output driver ('-ao help' for a list)

 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)

 dvd://<titleno>  play DVD title from device instead of plain file

 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)

 -ss <position>   seek to given (seconds or hh:mm:ss) position

 -nosound         do not play sound

 -fs              fullscreen playback (or -vm, -zoom, details in the man page)

 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)

 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)

 -playlist <file> specify playlist file

 -vid x -aid y    select video (x) and audio (y) stream to play

 -fps x -srate y  change video (x fps) and audio (y Hz) rate

 -pp <quality>    enable postprocessing filter (details in the man page)

 -framedrop       enable frame dropping (for slow machines)



Basic keys: (complete list in the man page, also check input.conf)

 <-  or  ->       seek backward/forward 10 seconds

 down or up       seek backward/forward  1 minute

 pgdown or pgup   seek backward/forward 10 minutes

 < or >           step backward/forward in playlist

 p or SPACE       pause movie (press any key to continue)

 q or ESC         stop playing and quit program

 + or -           adjust audio delay by +/- 0.1 second

 o                cycle OSD mode:  none / seekbar / seekbar + timer

 * or /           increase or decrease PCM volume

 x or z           adjust subtitle delay by +/- 0.1 second

 r or t           adjust subtitle position up/down, also see -vf expand



* * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *
```

So I went through the menu and opened it up and tired to play .flv and .asf (the only kind I have handy right now) files and I got back a "Fatal error!" window which said: Error opening/ initializing the selected video_out (-vo) device.

typing -vo help in the terminal just returned that -vo was an unknown command.

Any thoughts?

BTW I did try changing from US server to Main server as per another thread and it said something about 42 updates, but nothing seemed to be installed.

Later.

---

### Post by lol197282 on 2008-06-08
problem: radio feeds crashing rhythmbox on startup
the fix below did the trick.
cheers to the below post


> **RAOF said:**
> The file **rhythmdb.c** is where in the RhythmBox **source code** the error is.  It won't be on your system.

But the error seems to be in your database, or at least in reading it.  Perhaps you should regenerate it, and see if that works.  Try
```
mv ~/.gnome2/rhythmbox ~/rhythmbox-backup
```
and then start Rhythmbox again.  I think that's the right directory; it might be some other one inside the ~/.gnome2 directory if it isn't.

---

