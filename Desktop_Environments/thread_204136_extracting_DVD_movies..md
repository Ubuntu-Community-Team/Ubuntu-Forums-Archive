---
title: "extracting DVD movies."
date: 2006-06-26
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-26
Hello!

I have recently been extracting music using 'Ripper x'.  and exporting as 'WVA'.

My question is...

Is there a Linux Application that can extract DVD's?

Thanks!

---

### Post by hod139 on 2006-06-26
you can use mencoder.  A really good howto is here:
[http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder](http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder)

---

### Post by randell6564 on 2006-06-26
Thanks Hod!

I'll give it a shot!

---

### Post by randell6564 on 2006-06-26
[QUOTE=hod139]you can use mencoder.  A really good howto is here:
[http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder](http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder)[/QUOTE]

The link seems to be broken. Nothing ever loads. (sorry)

---

### Post by hod139 on 2006-06-26
Strange, the site must have just went down.  Well, a quick google search found these sites:
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html)
[http://axljab.homelinux.org/Mencoder_DVD_to_MPEG-4](http://axljab.homelinux.org/Mencoder_DVD_to_MPEG-4)
The first is from the developers from mencoder, so it probably very good.  Not sure about the second.

---

### Post by randell6564 on 2006-06-26
[QUOTE=hod139]Strange, the site must have just went down.  Well, a quick google search found these sites:
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html)
[http://axljab.homelinux.org/Mencoder_DVD_to_MPEG-4](http://axljab.homelinux.org/Mencoder_DVD_to_MPEG-4)
The first is from the developers from mencoder, so it probably very good.  Not sure about the second.[/QUOTE]

Thanks My Friend!

I just hope that it's not Too difficult. (being a newb and all!)  Was hoping for something that I could just apt-get or install from Synaptic.

Tryed to install a tarball earlier and got all kinds of confused! lol!  Anyway...

Thanks!

---

### Post by hod139 on 2006-06-26
Mencoder is in the repositories.  It is in the multiverse section, which is not enabled by default.

---

### Post by randell6564 on 2006-06-26
[QUOTE=hod139]Mencoder is in the repositories.  It is in the multiverse section, which is not enabled by default.[/QUOTE]


Yeah...

I found it.  (I didnt even look before I asked! Sorry)

But now that I have installed it, I cant FIND it!  It does not show up in the menu.

How do ya start it?  Sorry my friend...

I'm a newb to anything but point and click!

I DO know my way around Ubuntu somewhat.  I enabled the Universe/Multiverse Repo's as soon as I installed Ubuntu. I Just am not yet familiar with the various apps offered!

Usually when I install an app, I can 'killall gnome-panel' and that app will show up in the menu.  OR type the name of the app at the terminal and start it that way.

I did just that with mencoder and Nothing happened!

---

### Post by hod139 on 2006-06-26
There is not menu entry for mencoder, nor a gui frontend.  The encoder is really powerful, but you are forced to use the terminal and command line.  I would also suggest you install mencoder-??? where you replace ??? with your specific arch.  For example, if you have a modern pentium, install mencoder-686.

Once installed, you can open up a terminal and type mencoder.  On my system I get:
```

$ mencoder
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing cmdline)
$

```

Also, the gentoo wiki seems to be up again.  Skip the requirements section, as that is gentoo specific.

---

### Post by blanc11 on 2006-06-26
I beleive there is a program called DVDShrink that works pretty well, but I am not sure whether or not it is still in the repositories.

---

### Post by randell6564 on 2006-06-26
[QUOTE=hod139]There is not menu entry for mencoder, nor a gui frontend.  The encoder is really powerful, but you are forced to use the terminal and command line.  I would also suggest you install mencoder-??? where you replace ??? with your specific arch.  For example, if you have a modern pentium, install mencoder-686.

Once installed, you can open up a terminal and type mencoder.  On my system I get:
```

$ mencoder
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing cmdline)
$

```

Also, the gentoo wiki seems to be up again.  Skip the requirements section, as that is gentoo specific.[/QUOTE]



Then I did it right!

[B]root@shop:~# mencoder
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Irwindale (Family: 15, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing cmdline)
[/B]

But NOW, How to use it!  Now that I have it, am I just suppose to slip in a DVD and go from there?  HHMMF!

---

### Post by indytim on 2006-06-26
I believe DVDShrink is the windows-based app for extracting DVDs.  There is a Linux equivalent (haven't tried it yet). Sorry the name of the app escapes me at the moment.

IndyTim

---

### Post by scxtt on 2006-06-26
try DVD::Rip (dvdrip) ... it's in the repos - and works well ...

---

### Post by gingermark on 2006-06-26
[QUOTE=indytim]I believe DVDShrink is the windows-based app for extracting DVDs.  There is a Linux equivalent (haven't tried it yet). Sorry the name of the app escapes me at the moment.[/QUOTE]
The DVDShrink-style app for Linux is k9copy, although I understand DVDShrink works well in Wine.

---

### Post by blanc11 on 2006-06-26
I thought I came accross it in a repository somewhere, oh well, maybe I am wrong.

---

### Post by hod139 on 2006-06-27
[quote=randell6564]
But NOW, How to use it!  Now that I have it, am I just suppose to slip in a DVD and go from there?  HHMMF![/quote] 
Exactly!  Put in the DVD, and then do the following (taken from the gentoo wiki):
Run the following two commands to start ripping but be sure to change the "#" to the number of the dvd title that you want to rip (normally 1 but this can somtimes be the copyright notice or trailer). If you leave the # blank, it will rip the largest video track on the disc. 
 ```
mencoder dvd://# -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
mencoder dvd://# -ovc xvid -xvidencopts pass=2 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi


```"alang en" is in there because certain dvd's will give you the directors commentary if you dont specify the audio language specificaly. 
Now go find something to do because it will take a long time.

---

### Post by randell6564 on 2006-06-27
[QUOTE=hod139]Exactly!  Put in the DVD, and then do the following (taken from the gentoo wiki):
Run the following two commands to start ripping but be sure to change the "#" to the number of the dvd title that you want to rip (normally 1 but this can somtimes be the copyright notice or trailer). If you leave the # blank, it will rip the largest video track on the disc. 
 ```
mencoder dvd://# -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
mencoder dvd://# -ovc xvid -xvidencopts pass=2 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi


```"alang en" is in there because certain dvd's will give you the directors commentary if you dont specify the audio language specificaly. 
Now go find something to do because it will take a long time.[/QUOTE]

Your Awsome, Thanks alot!  Thanks to all of you!

---

### Post by douga on 2006-06-27
[QUOTE=gingermark]The DVDShrink-style app for Linux is k9copy, although I understand DVDShrink works well in Wine.[/QUOTE]

DVDShrink works very well in Wine. You can use dvdbackup to rip to hard disk, then DVDShrink to make it fit on a single-layer DVD.

---

### Post by visvak on 2006-06-27
the version for ubuntu is called xDVD Shrink and is by far the best DVD ripping application i have come across on any platform. i'm not 100% sure but mostly, its not there in the repos. Sourceforge link - 

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

---

### Post by randell6564 on 2006-06-27
[QUOTE=visvak]the version for ubuntu is called xDVD Shrink and is by far the best DVD ripping application i have come across on any platform. i'm not 100% sure but mostly, its not there in the repos. Sourceforge link - 

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)[/QUOTE]

Well...

I would like to try it but it comes as a .tar.gz and I'm not sure how to install tar.gz.

Hey Hod...I put in a dvd, fired up 'Mencoder' and entered the commands that you provided. I did not get any messege informing me that mencoder was now ripping the dvd.  Is that normal?  The little light on the cdrom was blinking, indicating that something was happening but other than that, I really cant tell if it is copying the dvd!

---

### Post by master_b on 2006-06-27
Acidrip - rip whole or part of DVD - good for ripping audio tracks from Music Video DVDs.

or I use K9Copy  - but I copy whole DVD to .iso on hard disk.

Bill

---

### Post by hod139 on 2006-06-28
[quote=randell6564]
Hey Hod...I put in a dvd, fired up 'Mencoder' and entered the commands that you provided. I did not get any messege informing me that mencoder was now ripping the dvd.  Is that normal?  The little light on the cdrom was blinking, indicating that something was happening but other than that, I really cant tell if it is copying the dvd![/quote]

What do you mean fired up mencoder?  You should put in the dvd, and then enter the commands into a terminal.  There is no starting mencoder first.  I'm also not sure what kind of status messages it outputs.

If you want a gui, you can install [acidrip]("http://untrepid.com/acidrip/"), which is a front end for mplayer and mencoder. In a terminal type
```
sudo apt-get install acidrip
```
or search for it in synaptic.   I have never used it though.

---

### Post by visvak on 2006-06-30
[QUOTE=randell6564]Well...

I would like to try it but it comes as a .tar.gz and I'm not sure how to install tar.gz.

Hey Hod...I put in a dvd, fired up 'Mencoder' and entered the commands that you provided. I did not get any messege informing me that mencoder was now ripping the dvd.  Is that normal?  The little light on the cdrom was blinking, indicating that something was happening but other than that, I really cant tell if it is copying the dvd![/QUOTE]

there's also an optiion to download a noarch.rpm file. get that. then use - 

```
sudo alien [the full name of the file]
``` 

it will get converted to a .deb file which u can install through gDebi installer that is there in the applications > system tools menu

---

### Post by randell6564 on 2006-06-30
[QUOTE=hod139]What do you mean fired up mencoder?  You should put in the dvd, and then enter the commands into a terminal.  There is no starting mencoder first.  I'm also not sure what kind of status messages it outputs.

If you want a gui, you can install [acidrip]("http://untrepid.com/acidrip/"), which is a front end for mplayer and mencoder. In a terminal type
```
sudo apt-get install acidrip
```
or search for it in synaptic.   I have never used it though.[/QUOTE]

Sorry, I meant that I inserted a dvd and then typed 'mencoder' at the terminal and then entered the commands that you provided.

After doing that, I did not get any messeges that would indicate that the burning process had started.

---

### Post by hod139 on 2006-06-30
[quote=randell6564]Sorry, I meant that I inserted a dvd and then typed 'mencoder' at the terminal and then entered the commands that you provided.
[/quote]

Maybe it is just the way you wrote the post, but it sounds possibly incorrect.  You should not be typing mencoder and pressing enter.  You should type (or copy) the entire line, then press enter. Using some terminology, mencoder is the application, and everything on the right hand side are arguments.  The idea is to pass all those arguments to mencoder.  If you press enter after mencoder, the argument list is empty.

Maybe I am misinterpreting your post?

---

### Post by randell6564 on 2006-06-30
[QUOTE=hod139]Maybe it is just the way you wrote the post, but it sounds possibly incorrect.  You should not be typing mencoder and pressing enter.  You should type (or copy) the entire line, then press enter. Using some terminology, mencoder is the application, and everything on the right hand side are arguments.  The idea is to pass all those arguments to mencoder.  If you press enter after mencoder, the argument list is empty.

Maybe I am misinterpreting your post?[/QUOTE]

Gotcha! I WAS doing it wrong, Sorry bout that!  I was attempting to START mencoder like you would start an app useing the terminal.  I would type 'mencoder' then hit enter THEN enter the commands for burning.

---

### Post by hod139 on 2006-06-30
Glad you got it working :D.  Have you tried the AcidRip gui?  I'm half way curious if it is any good.

---

### Post by randell6564 on 2006-06-30
[QUOTE=hod139]Glad you got it working :D.  Have you tried the AcidRip gui?  I'm half way curious if it is any good.[/QUOTE]

AS a matter of fact, I was JUST checking it out before I got your reply just now.

Cant tell ya much because even though it might be in nice gui format, I still dont know what the hell im doing! lol!

I loaded a dvd to it and clicked start and it dissapeared!  So I started it again and played around with the viewing still shots of the movie and then it froze up on me!

I'm sure that I am suppose to enter some info before starting to extract it but all the options are greek to me, so there ya go!

---

### Post by randell6564 on 2006-06-30
Hey hod, I'm trying mencoder again. (o-boy!)

Heres the output:

[B]scott@shop:~$ mencoder dvd://1 -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Irwindale (Family: 15, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
Reading disc structure, please wait...
There are 1 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
success: format: 0  data: 0x0 - 0xf67dc800
Selected DVD audio channel: 128 language: en
mencoder dvd://1 -ovc xvid -xvidencopts pass=2 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi

[/B]

Nothing happens after this to give me an indication that it is now copying the dvd. is that normal?  I now just have a blinking cursor.

---

### Post by hod139 on 2006-06-30
Looking closely at your output:

[quote=randell6564][B]
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread3/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
[/B][/quote]
We see that you do not have libdvdcss installed.  Reading the file pointed to in that error message, to install libdvdcss type the following into a terminal:
```

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

Then try mencoder again.

---

### Post by randell6564 on 2006-06-30
[QUOTE=hod139]Looking closely at your output:


We see that you do not have libdvdcss installed.  Reading the file pointed to in that error message, to install libdvdcss type the following into a terminal:
```

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

Then try mencoder again.[/QUOTE]

Yeah I got it after reading the CLEARLY shown readme file! lol!  (I need ta slow down!)

Thought the wine would help! :P  I'll post the results now that css is installed, Thanks!

I just noticed that ya tryed to send me a private messege but i couldnt open it (somthing about a possible pop-up blocker)  I'm not aware of any pop-up blocker but then thats a whole other issue!

---

### Post by randell6564 on 2006-06-30
Well...

Here is the output now, after installing css:

[B]scott@shop:~$ mencoder dvd://1 -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Irwindale (Family: 15, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
libdvdread: Using libdvdcss version 1.2.5 for DVD access
Reading disc structure, please wait...
There are 1 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
Cannot open the IFO file for DVD title 1.
File not found: '1'
Failed to open dvd://1
Cannot open file/device.[/B]

I can see that it has something to do with the '1' that I entered.  But I dont know what else I can enter in place of the '1'.

The only thing that is visible on the disc label is the name of the movie, Columbia Pictures, PG rating, DVD video logo and a little square with the number 1 inside of it.

This is gonna be FUN! :)

---

### Post by randell6564 on 2006-06-30
OK...

Leaving the # blank instead of entering the '1' worked!  YEAH!! :'

We're OFF!  :grin:   (of course, until I need you to help me burn the copy to a dvd disk. :P)

Can you make the copy an iso?

---

### Post by randell6564 on 2006-07-01
Well my Friend...

I Waited an hour for the dvd to be copied!

Now, in my Home folder, there is three files... One is named,** 'Charlie Bronson-1.avi'**

And another one is named, **'dvd_video.avi'  **  

The third one is named, **'divx2pass.log'**

The two avi's are **Text files **and the other is a **'Application Log'**

WA,WA, HUH?

Did mencoder copy the movie to a filesystem folder that I am not aware of yet?

---

### Post by hod139 on 2006-07-01
Did you run the second pass?
```

mencoder dvd://# -ovc xvid -xvidencopts pass=2 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi

``` 
Also, most of your questions can be answered on this wiki:
[http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder]("http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder")


For example:

> You can run this command to find the number that corresponds to the title you actualy want to rip 
 mplayer dvd://1

There are also the other 2 links I posted earlier in this thread.  If you have questions after reading the external sites, feel free to post another message.

---

### Post by randell6564 on 2006-07-01
Thanks hod!  I'll post back after reading the links that you provided.

I think that I might have missed a step (the second pass) because after entering the first command, it took off!
Started counting down and took about an hour to stop so I thought that I had it.

Think I was suppose to enter the second command AFTER it finished with the first! :P

---

### Post by randell6564 on 2006-07-04
Well...
 allow me to show the output of the first command because something is definately happening when I enter: **mencoder dvd://1 -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null**
output:
[B]1 duplicate frame (s)!
pos: 131.3s 3986f (2%) 29.fps Trem: 108min 1593mb A- V:0.001 [1620:192][/B]

This is what takes place repeatedly on the terminal screen.  it's obveously counting down, but I do not get a chance to enter the second command:

**mencoder dvd:// -ovc xvid -xvidencopts pass=2 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi**

until the first is done!  Then once the second command is completed nothing happens and I end up with what looks to be a movie file in my home folder but after checking, it is actually a text file!

---

### Post by randell6564 on 2006-07-04
im trying to upload a screenshot from my terminal but not sure just how to do it!

Ok... here is the output screenshot of the first command

---

### Post by yabbadabbadont on 2006-07-04
Just out of curiosity, which DVD are you trying to backup?  I found that the new "Underworld Evolution" disc uses a new version of Sony's copy protection.  (I'm not talking about CSS either, by the way)  None of the linux based rippers I tried could read it.  (I think they all use libdvdread and it couldn't handle the new protection scheme)  Even the old trusty windows DVDDecrypter couldn't handle it.  (it isn't developed anymore)  I ended up using a different windows based ripper to make a full backup.  (DVDFabDecrypter, thank goodness for videohelp.com)

---

### Post by randell6564 on 2006-07-04
[QUOTE=yabbadabbadont]Just out of curiosity, which DVD are you trying to backup?  I found that the new "Underworld Evolution" disc uses a new version of Sony's copy protection.  (I'm not talking about CSS either, by the way)  None of the linux based rippers I tried could read it.  (I think they all use libdvdread and it couldn't handle the new protection scheme)  Even the old trusty windows DVDDecrypter couldn't handle it.  (it isn't developed anymore)  I ended up using a different windows based ripper to make a full backup.  (DVDFabDecrypter, thank goodness for videohelp.com)[/QUOTE]

Hi!
Well... if you're talking about the name of the movie, it's called, 'Hard Times' starring Charles Bronson and James Cobern.

It's an old movie.  I can give you everything that is printed on the disc label if that would help! 

(Killer Movie BTW!)

"DVDfabdecrypter"  is that something that Ubuntu can use?

---

### Post by yabbadabbadont on 2006-07-04
Not natively.  It is a windows application.  I haven't tried it yet, but it might run under wine.  Since I couldn't get it to work in linux, and I dual boot with win2k, I just used windows tools to do the job.  I am, however, very careful to turn off my DSL modem *before* booting into windows...  it's the only safe way to use it.  ;)

---

### Post by randell6564 on 2006-07-04
[QUOTE=yabbadabbadont]Not natively.  It is a windows application.  I haven't tried it yet, but it might run under wine.  Since I couldn't get it to work in linux, and I dual boot with win2k, I just used windows tools to do the job.  I am, however, very careful to turn off my DSL modem *before* booting into windows...  it's the only safe way to use it.  ;)[/QUOTE]

I dont understand...

Why do you have to kill the modem?  And where can I find this application and the documentation for it?

Thanks!

---

### Post by yabbadabbadont on 2006-07-04
Windows is pretty much completely unsecure and I have a broad-band connection.  Since I don't feel like screwing around with "windows genuine advantage" and all the security updates, I just turn the modem off so that there isn't a network connection to worry about.

[http://www.videohelp.com/tools?tool=DVDFab_Decrypter](http://www.videohelp.com/tools?tool=DVDFab_Decrypter)

There is a *lot* of information on that site on the different video formats and standards as well as howto guides.

---

### Post by randell6564 on 2006-07-04
[QUOTE=yabbadabbadont]Windows is pretty much completely unsecure and I have a broad-band connection.  Since I don't feel like screwing around with "windows genuine advantage" and all the security updates, I just turn the modem off so that there isn't a network connection to worry about.

[http://www.videohelp.com/tools?tool=DVDFab_Decrypter](http://www.videohelp.com/tools?tool=DVDFab_Decrypter)

There is a *lot* of information on that site on the different video formats and standards as well as howto guides.[/QUOTE]

Thanks!  Now I know what ya mean!  I've had my fricken Windows cd for OVER a year and EVERY-SINGLE-TIME that I want to re-install or reformat, I have to activate it by calling Bum$%*&egypt somewhere and talking to someone that I cant even understand!

A cd that I OWN supposedly!  I swear, if i knew how to burn an exact copy of windows, i'd give them away by the hundreds!

Thanks Again My Friend!

---

### Post by echo $USER on 2006-07-04
This is the best there is...

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

And it is not the windows version, runs natively  in linux.

---

### Post by randell6564 on 2006-07-04
[QUOTE=echo $USER]This is the best there is...

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

And it is not the windows version, runs natively  in linux.[/QUOTE]

Thanks alot!  But now that I have finally figured out how to install it,  How in the heck do ya USE it?

I stuck a dvd in, started DVDshrink,    clicked on 'Start copy' and a window flashed for a second and then I'm here, wondering if it started burning.

I know that i'm suppose to enter some things in the boxes like a title for the project, etc...

but i'm not sure what "enter the audio channel to rip" and  what all the little boxes on the right mean so i just left them blank.

Know where a newb can go to learn how to use it?

---

### Post by randell6564 on 2006-07-04
Hey Echo, Thanks again!  I found the 'how to's' at the DVDshrink web page.

Time to do some homework!  See ya!

---

### Post by echo $USER on 2006-07-05
I've never used the GUI.  I just throw the dvd in and a blank then run dvdshrink from the command line.  Thirty minutes later, my dup is ready.  And that is burning at 2X.

And be advised that it does not do a complete copy of a DVD but only of the main title, ONE audio track and ONE subtitle track.  But hey, thats all i want; muck the previews.

---

### Post by randell6564 on 2006-07-06
Thanks My Friend!

---

