---
title: "few questions =) dpi and radio"
date: 2009-02-07
forum: General Help
---

### Post by Ishai Cohen on 2009-02-07
hi
since i started using ubuntu (2 days ago)
everything i needed to ask i tried by myself
i read guids all night and in the end i already learn what i need :p
my thinking is that i only ask for help after i dont got anyway of doing it myself

and now i rly need your help guys

first thing is that i need to watch few sites on internet explorer
i tried few plug-ins for firefox but it seem to fail :d

second is that i got a radio server for 500 ppl
and im shoutcasting matches between teams in the game i play (enemy territory) and today there is important game
so on xp i used winamp + plug-in to connect to the server (ip:port and password) and thats it, shoutcast to 500 ppl :)
the game of course !
with my microphone

third question is mouse DPI
i have a Razer DeathAdder
now i have tried all those configs guids there are but they all failed, how i know? i put the mouse wheel light on "false" and its still glowing :>

now, so far i only know the linux community is very supportive which i very admire

if i broke the rules with opening this thread, plz say to me =)

have a good day, Cohen.

---

### Post by mb_webguy on 2009-02-07
It's generally better to make separate threads for separate problems.  You'll get better better responses that way.

For your first problem, i.e. sites that require IE (see what I did there?  hehe)...  You need IE.  It's that simple.  While they should know better by now, some clueless web designers still use ActiveX controls or other Microsoft-proprietary, IE-specific content on their websites, which requires users to either use IE or go to a different website.  Since about only about 2/3 of people regularly use IE as their browser, that's a significant portion of their customer base they're excluding, which isn't very good business sense.  But I digress...

You can install IE on Linux using [Wine]("http://www.winehq.org/download/deb") and a little installer called, conveniently, [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").  You can choose from several versions of IE to install (hence "IE**s**4Linux" rather than "IE4Linux").  It's not perfect, but it works for when you absolutely must use IE.

As for your second question...  I'm not quite sure what you're asking.  You have a game... it involves microphones... and you used Winamp to shoutcast to your friends.  Um, congratulations?  Seriously though, I'm really not sure what you're asking.  And I'm pretty sure you didn't even actually ask a question.  Various applications can act as a shoutcast client to play shoutcast video or Internet radio.  Or do you want to set up a shoutcast server?  There are several options available for that as well.  I don't have a lot of experience with shoutcast except from the client side, but if I knew exactly what you're wanting to do, I might be better able to help.

And as to your third question...  I have no clue.  I have a Razr v3xx, which I modded about a year ago when I first got it.  I don't remember exactly what I did or how I did it, and even if I could remember, it probably wouldn't work with your Razr.  Sorry.

---

### Post by Ishai Cohen on 2009-02-07
> **mb_webguy said:**
> It's generally better to make separate threads for separate problems.  You'll get better better responses that way.

For your first problem, i.e. sites that require IE (see what I did there?  hehe)...  You need IE.  It's that simple.  While they should know better by now, some clueless web designers still use ActiveX controls or other Microsoft-proprietary, IE-specific content on their websites, which requires users to either use IE or go to a different website.  Since about only about 2/3 of people regularly use IE as their browser, that's a significant portion of their customer base they're excluding, which isn't very good business sense.  But I digress...

You can install IE on Linux using [Wine]("http://www.winehq.org/download/deb") and a little installer called, conveniently, [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").  You can choose from several versions of IE to install (hence "IE**s**4Linux" rather than "IE4Linux").  It's not perfect, but it works for when you absolutely must use IE.

As for your second question...  I'm not quite sure what you're asking.  You have a game... it involves microphones... and you used Winamp to shoutcast to your friends.  Um, congratulations?  Seriously though, I'm really not sure what you're asking.  And I'm pretty sure you didn't even actually ask a question.  Various applications can act as a shoutcast client to play shoutcast video or Internet radio.  Or do you want to set up a shoutcast server?  There are several options available for that as well.  I don't have a lot of experience with shoutcast except from the client side, but if I knew exactly what you're wanting to do, I might be better able to help.

And as to your third question...  I have no clue.  I have a Razr v3xx, which I modded about a year ago when I first got it.  I don't remember exactly what I did or how I did it, and even if I could remember, it probably wouldn't work with your Razr.  Sorry.

1) when i had xp and i have a IE tab plug-in for firefox, worked great :>
but its not avi on linux

2) my question is-how i connect to a radio server and shoutcast
not music, how to shoutcast like those football announcer, broadcaster ?

---

### Post by mb_webguy on 2009-02-07
There are various applications available for setting up a shoutcast server, but I think all you need is the DSP plugin.  I noticed that there is a Linux version of the DSP plugin available on the [Shoutcast website]("http://www.shoutcast.com/download").  Look at the bottom of the section talking about the Winamp plugin, where it says "Instructions - Unix, Linux & MAC OSX".  There's a link to download it.  

I didn't put it on my system, but I downloaded it and took a look at it in the archive manager.  It doesn't come with any instructions, but from what I can tell, you just need to extract the tarball (that's the .tgz file, which is like a zip file), and run it.  There are a couple of configuration files (which may need configuring), and three binaries (or scripts, I didn't check): one each for Unix, Linux, and BSD.  You'd want the Linux one, of course, and delete the other two.

---

### Post by zzzuppermen on 2009-02-07
Hi!

The Firefox IE plugin simply invokes an embedded IE window in Firefox. Simply put, it's the "lazy" solution to copying the address, open IE, paste the address, hit Enter. So, no Windows = no IE. Unless IEs4Linux ;)

To stream audio over the internet, you need:
1. Source server (from where the audio originates)
2. Streaming server (a machine with highspeed internet connection)
3. Clients ("500 ppl")

The source and streaming server can be on the same machine, but since you've mentioned that you are connecting to a server from Winamp, I assume you have access to a separate streaming server. All you need to do is know your username and password and set up a source server.

Here's a howto on Shoutcast on Ubuntu:
[http://ubuntuforums.org/showthread.php?p=1804752]("http://ubuntuforums.org/showthread.php?p=1804752")

---

### Post by Ishai Cohen on 2009-02-07
> **zzzuppermen said:**
> Hi!

The Firefox IE plugin simply invokes an embedded IE window in Firefox. Simply put, it's the "lazy" solution to copying the address, open IE, paste the address, hit Enter. So, no Windows = no IE. Unless IEs4Linux ;)

To stream audio over the internet, you need:
1. Source server (from where the audio originates)
2. Streaming server (a machine with highspeed internet connection)
3. Clients ("500 ppl")

The source and streaming server can be on the same machine, but since you've mentioned that you are connecting to a server from Winamp, I assume you have access to a separate streaming server. All you need to do is know your username and password and set up a source server.

Here's a howto on Shoutcast on Ubuntu:
[http://ubuntuforums.org/showthread.php?p=1804752]("http://ubuntuforums.org/showthread.php?p=1804752")

yea lol i found that guid BUT
the download link is not avi xD
so im stuck on first step :)

edit: ok found it :~>
edit2: it doesnt work

---

### Post by zzzuppermen on 2009-02-07
I will look into it. I use Liveice as source server for an IceCast2 streaming server. But that's different. In the meantime, you can search Synaptic for "shoutcast", I'm pretty sure they have something that you can install with APT. Also, if you want more results, you can try

```
sudo apt-cache search shoutcast
```

---

### Post by Naiki Muliaina on 2009-02-07
To broadcast a shoutcast playlist to a server follow the link in my sig. I believe to run it from a mic you need to add your mic to the playlist. If its pre recorded, cool just add pre recorded sounds to your playlist. If its live thats something else.

I was told how to do it, cant remember exactly how i did it. You had to add the path off the mics input to your playlist i think. I had a USB mic and i had to add in a path from /dev. It worked perfectly fine, whatever i did worked first time with no fiddling required. Cant remember what file i added though, and if it will be the same for jack mics etc.

*Edit*

Ok, may need someone more techy to confirm this, but i think /dev/dsp is your line in if you are using a mic that just uses the normal line-in plug. So, follow the instructions in my sig, but your playlist should just be:

/dev/dsp
/dev/dsp

Again, will need someone to confirm thats the line in for a mic.

---

### Post by zzzuppermen on 2009-02-10
Quick note on audio IO.
/dev/dsp is the OSS sound device. If you use ALSA, it can be found under /dev/snd/
The catch is that /dev/dsp is an OSS compatibility layer for ALSA, so eventualy it runs only on ALSA. If your sound card has troubles with OSS, try to use the one from /dev/snd/

The files are named like "pcm" + "C" + card id + "D" + device id + function. So the first capture device of your first sound card would be "pcmC0D0c". If you have only one soundcard it's easy.

To list all available options, just do a ```
ls -l /dev/snd/
```

---

### Post by Naiki Muliaina on 2009-02-11
Thanks for that :) Im going to have to have a play with that at some point :)

---

