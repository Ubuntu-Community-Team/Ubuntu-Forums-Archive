---
title: "The CLI-only quest"
date: 2009-01-16
forum: General Help
---

### Post by NeonBible on 2009-01-16
Help me on my quest to go completely CLI and not use X at all!

This is not permanent.  I simply doing this for fun and to learn a bit more about CLI.

A few beginner questions:

1) Whats the best way to get out of Gnome and into CLI? I have tried "/etc/init.d/gdm stop" but that hangs the UI and I have Ctrl-Alt-Del to reset.

2) How do I boot directly into CLI when I start Ubuntu?

3) When I am using CLI, can run concurrent applications? E.g. run Cmus and use other apps while I'm listening to MP3s.

4) If I kill gnome, do I still have sounds drivers like ALSA, OSS, Pulse loaded?

If I can't do (3) then I might just quit my quest lol.

Here are the apps I am using so far:

Vim - awesome!
Mutt - awesome!!
Cmus - Hmm haven't fully figured out but looks good
Elinks - not sure if I can get used to text based browsing.  I'm not missing images, but just the amount of crap I need to go through to get to a link.

I am looking for the best of the following:

MSN
RSS Reader

and anything cool you can recommend ;)

Ok now some q's about specific apps

Cmus
----
1) how do I change volume?
2) is it me of or is the playlist buggy? skipping tracks with 'z' and 'b' keys seems totally random.  When a song finishes it doesn't always go to the next one in the list.  Whats the difference playlist and play queue?

Elinks
------

1) Are there quicker ways of navigating through pages?
2) Apparently this supports tables, frames and CSS. It doesn't look that way to me.  I have seen screenshots where everything looks like on a graphical browser (in terms of formatting) but all in text obviously.  Am I supposed to enable this?

thanks :)

---

### Post by donkyhotay on 2009-01-16
I personally use yakuake within X for when I need the CLI, makes it easier to jump between CLI's. If you really need that 'old school' look then just use ctrl-alt-f# where # is pretty much any number between 1 and 6 and you'll be out of the GUI entirely. Going back is easy by just hitting ctrl-alt-f7.

---

### Post by jonobr on 2009-01-16
Some hopefully useful answers

```
Whats the best way to get out of Gnome and into CLI?
```
Did you try cntrl - alt -F1

Login and then exit to go back to gui


```
How do I boot directly into CLI when I start Ubuntu?
```

Think you need to go to menu.list and modify, recommend you research that one though!!

```
When I am using CLI, can run concurrent applications? 
```

Try running the app as a background task
ie.
./myapp &

---

### Post by bodhi.zazen on 2009-01-16
> **NeonBible said:**
> Help me on my quest to go completely CLI and not use X at all!

This is not permanent.  I simply doing this for fun and to learn a bit more about CLI.

A few beginner questions:

1) Whats the best way to get out of Gnome and into CLI? I have tried "/etc/init.d/gdm stop" but that hangs the UI and I have Ctrl-Alt-Del to reset.

Ctrl-Alt-F1

> 2) How do I boot directly into CLI when I start Ubuntu?

sudo mv /etc/init.d/S20gdm /etc/init.d/s20gdm

> 3) When I am using CLI, can run concurrent applications? E.g. run Cmus and use other apps while I'm listening to MP3s.

Use screen :twisted:

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

> 4) If I kill gnome, do I still have sounds drivers like ALSA, OSS, Pulse loaded?

yes

> If I can't do (3) then I might just quit my quest lol.

:lolflag:

> Here are the apps I am using so far:

Vim - awesome!
Mutt - awesome!!
Cmus - Hmm haven't fully figured out but looks good
Elinks - not sure if I can get used to text based browsing.  I'm not missing images, but just the amount of crap I need to go through to get to a link.

I am looking for the best of the following:

MSN
RSS Reader

and anything cool you can recommend ;)

Ok now some q's about specific apps

Cmus
----
1) how do I change volume?
2) is it me of or is the playlist buggy? skipping tracks with 'z' and 'b' keys seems totally random.  When a song finishes it doesn't always go to the next one in the list.  Whats the difference playlist and play queue?

Elinks
------

1) Are there quicker ways of navigating through pages?
2) Apparently this supports tables, frames and CSS. It doesn't look that way to me.  I have seen screenshots where everything looks like on a graphical browser (in terms of formatting) but all in text obviously.  Am I supposed to enable this?

thanks :)

[http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html](http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html)

[http://ubuntuforums.org/showthread.php?t=833627](http://ubuntuforums.org/showthread.php?t=833627)

---

### Post by -grubby on 2009-01-16
I'm not trying to offend you here, but you may not be ready to go CLI-Only. I mean, you don't know how to quit Gnome, you don't know whether or not you can run 1+ apps in the terminal at a time, you seem to think Gnome runs the sound server, etc... :|

---

### Post by bodhi.zazen on 2009-01-16
> **nathangrubb said:**
> I'm not trying to offend you here, but you may not be ready to go CLI-Only. I mean, you don't know how to quit Gnome, you don't know whether or not you can run 1+ apps in the terminal at a time, you seem to think Gnome runs the sound server, etc... :|

a journey of 10,000 miles starts with the first step :twisted:

---

### Post by drubin on 2009-01-16
> **bodhi.zazen said:**
> a journey of 10,000 miles starts with the first step :twisted:

tooo true

---

### Post by -grubby on 2009-01-16
> **bodhi.zazen said:**
> a journey of 10,000 miles starts with the first step :twisted:

And he's starting with the 200th step...

---

### Post by snova on 2009-01-16
> **bodhi.zazen said:**
> a journey of 10,000 miles starts with the first step :twisted:

Allow me to suggest reading up on shell jobs to begin with (running multiple programs at the same time).

If you start a program like so:

```
command **&**
```

It will be run in the background, so you can continue doing something else. Unfortunately, any messages it prints to the terminal will be written anyway, which can get in the way of your prompt. This will redirect all output to /dev/null (a kind of black hole):

```
command **&>** /dev/null
```

Combine them. ;)

Also, if you start a program and later decide to move it to the background, you can press Ctrl-Z to suspend it. Then either run "fg" to return it to the foreground (take over again) or "bg" to move it to the background (equivalent to a & when you initially ran it).

Oh, and by the way, there are six (at least) terminals available, not just one. ;) Ctrl-Alt-F1, F2, F3, ... F7 is Gnome.

---

### Post by donkyhotay on 2009-01-16
> **nathangrubb said:**
> I'm not trying to offend you here, but you may not be ready to go CLI-Only. I mean, you don't know how to quit Gnome, you don't know whether or not you can run 1+ apps in the terminal at a time, you seem to think Gnome runs the sound server, etc... :|

While he's not ready to go CLI only in any productive capacity, it is however a good way to learn the system which is the OP's stated purpose here. Forcing yourself to only use the CLI will either help you quickly become proficient or turn you into the kind of gibbering wreck the nice young men in clean white coats end up hauling away. I definitely wouldn't recommend making any permanent changes on your only computer though. Otherwise if you need to get some actual work done on your system you'll be pretty much dead in the water.

---

### Post by collinp on 2009-01-16
> **bodhi.zazen said:**
> a journey of 10,000 miles starts with the first step :twisted:

Yes, but if you trip on your first step because of lack of knowledge, then the 10,000 mile journey will end as soon as it starts. Oh, and you will be dirty to boot.

---

### Post by Bucky Ball on 2009-01-16
NathanGrubb, OP wants to try the CLI route for fun and experimentation, not a permanent switch. OP will probably learn something along the way and one day make a switch or not. 

> This is not permanent.  I simply doing this for fun and to learn a bit more about CLI. 

... the second line of the OP's first post. Not sure how you missed it.

---

### Post by bodhi.zazen on 2009-01-16
> **snova said:**
> F7 is Gnome.


X = F7 :lolflag:

---

### Post by drubin on 2009-01-16
> **snova said:**
> Allow me to suggest reading up on shell jobs to begin with (running multiple programs at the same time).

If you start a program like so:

```
command **&**
```

It will be run in the background, so you can continue doing something else. Unfortunately, any messages it prints to the terminal will be written anyway, which can get in the way of your prompt. This will redirect all output to /dev/null (a kind of black hole):

```
command **&>** /dev/null
```

Minor correction 

```
command > /dev/null **&**
``` You need to tell it to send the buffer output to the "black void" before.. 

You could also re-direct error messages as well by.

```
command >  /dev/null 2>&1 **&**
```

Tells it to send error stream (2) to the same place as standard output (1)

---

### Post by snova on 2009-01-16
> **Hellow said:**
> Yes, but if you trip on your first step because of lack of knowledge, then the 10,000 mile journey will end as soon as it starts. Oh, and **you will be dirty to boot.**

Hey! You stole my quote! :P

> **bodhi.zazen said:**
> X = F7 :lolflag:

I know, but if he calls it Gnome, I'll call it Gnome.

Though technically, yes. X is the system that provides for the graphics, Gnome is essentially a large collection of programs working together to provide a nice desktop.

---

### Post by donkyhotay on 2009-01-16
Oh, and definitely install and use the 'screen' program. Although putting programs into the background/foreground works there are some programs that just doesn't work very well with.

---

### Post by snova on 2009-01-16
> **drubin said:**
> Minor correction 

```
command > /dev/null **&**
``` You need to tell it to send the buffer output to the "black void" before..

Interesting, I didn't know that.

> You could also re-direct error messages as well by.

```
command >  /dev/null 2>&1 **&**
```

Tells it to send error stream (2) to the same place as standard output (1)

Or you can use &> and redirect both at once. ;) (Though not all shells can do that...)

**1>** will redirect standard output, where most output goes. But error messages will often go to another place, standard error, which can be redirected via **2>**. **2>&1** will redirect the error output to the standard output, and combined with >/dev/null (1 is the default here), both streams will be redirected into nothingness.

---

### Post by -grubby on 2009-01-16
> **Bucky Ball said:**
> NathanGrubb, OP wants to try the CLI route for fun and experimentation, not a permanent switch. OP will probably learn something along the way and one day make a switch or not. 

That is the second line of the OP's first post. Not sure how you missed that.

I realize this. That does not mean my point is invalid... 

Note to OP: if you want to go back into x, run 'startx'

---

### Post by bodhi.zazen on 2009-01-16
> **snova said:**
> I know, but if he calls it Gnome, I'll call it Gnome.

Though technically, yes. X is the system that provides for the graphics, Gnome is essentially a large collection of programs working together to provide a nice desktop.

:lolflag:

---

### Post by drubin on 2009-01-16
Where is that report button..........: LOLFLAG :

---

### Post by NeonBible on 2009-01-18
Just wanted to say thanks for all the help.  Been running two days on CLI apps and I have to say haven't had this much fun with computer software for a long time.

Cmus is now my main music player.  Its far quicker to navigate with keyboard.  Just a shame it doesn't save my library if I unmount my storage drive.

I install all my apps with apt-get now instead of Synaptic manager.

Elinks is an awesome text web browser.  Gotta love the numbered links, that is genius.

Mutt, is simple and just works.

Stil haven't tried multiple terminals with Screen yet.

---

### Post by mcduck on 2009-01-18
> **NeonBible said:**
> 
Cmus is now my main music player.  Its far quicker to navigate with keyboard.  Just a shame it doesn't save my library if I unmount my storage drive.

You could try MPD with ncmpc as client. As long as you don't tell MPD to update it's library when the storage drive is unplugged it will keep your library.

As a bonus you can close ncmpc and the music will keep on playing. :)

---

### Post by NeonBible on 2009-01-18
> **mcduck said:**
> You could try MPD with ncmpc as client. As long as you don't tell MPD to update it's library when the storage drive is unplugged it will keep your library.

As a bonus you can close ncmpc and the music will keep on playing. :)

Awesome thanks.  Looks tricky to set up though but I will give it a whirl :)

---

### Post by mcduck on 2009-01-18
It's not that hard..

Install everything you need:
```
sudo apt-get install mpd ncmpc mpc
```
(If I remember right it might ask you if you wish to install MPD as a daemon. In that case answer "yes".)

Then link your music directory into MPD's default:
```
sudo ln -s /path/to/yourmusic /var/lib/mpd/music
```

...and, if you need to change sound output, set passwords or anything else, just edit /etc/mpd.conf. The configuration file has pretty good explanations for every setting. If you change any settings here you can restart MPD by running "sudo etc/init.d/mpd restart"

When done, run "mpc update" to create the library. After it finishes you are ready to enjoy your music.

If you have music in many different places (some on your computers internal drive and some on the removable drive) you can link your music directories into separate directories inside /var/lib/mpd/music.

---

### Post by NeonBible on 2009-01-18
Excellent, thanks again.

And going back to what you said abotu updating the library.  I think Cmus updates it on startup and if I forget to mount my internal NTFS drive then its bye bye entire library.

How do I set this up in mpd?

And is there anything I should know about it running in the background, you said music still plays.  How do I shut it down completely?  I guess this is related to it being a 'daemon'?

---

### Post by mcduck on 2009-01-18
MPD updates the library when you tell it to do that. Each client has it's own way to do it, but "mpc update" will do the trick, or in ncmpc you can press ctrl-u. MPD's music database is pretty quick one, that's one of the main reasons I started using it in the first place (all other players are too slow with my rather large music library..)

The music starts playing when you tell it to start (using any client you want) and stops when you tell it to stop. While playing, you don't need to have a client running, MPD will play the music on the playlist until told to stop (once again using any client you want).

You don't need to start or stop MPD itself, it will start automatically on boot and doesn't really use any resources when not playing anything.

In the end, you can use MPD clients just like any other music player and simply forget about MPD running in background if you want. Or you can enjoy the benefits of having a daemon that plays music to you, leave it playing when you shut down the machine so it'll continue from where you left on next boot even before you log in to the machine, use the same music library (actually the same music player!) from command line and with graphical clients (Sonata is great one) or even control it remotely from other computers..

---

### Post by lswb on 2009-01-18
Here's a link that explains how to add a text-only runlevel as a grub menu item.

[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)

You may also be interested in settup up framebuffer support in your vt for graphics display, and the gpm package which allows use of the mouse in a vt.

---

### Post by NeonBible on 2009-01-18
Works great!

But I was trying to specify user level settings using ~/mpdconf but its not picking up those settings.  I don't want to touch mpd.conf. Any ideas?

---

### Post by mcduck on 2009-01-19
> **NeonBible said:**
> Works great!

But I was trying to specify user level settings using ~/mpdconf but its not picking up those settings.  I don't want to touch mpd.conf. Any ideas?

If you installed it as a daemon (which is the normal way of using MPD) the only place to configure MPD is /etc/mpd.conf. It's a system service and runs as it's own user ("mpd") so it can't be configured at user level. (wouldn't really work on a multi-user setup, only one instance of MPD running but each user having their own configuration files..)

It *is* possible to setup MPD so that users can start and stop it and have their own configuration files, but that doesn't really have any benefits and is a lot harder to do than the normal setup. And you'd always need to start MPD before you can start any client program. In other words you'd loose pretty much all the benefits of MPD and make it harder to use than normal music players.

I really, really recommend keeping MPD as a daemon and using /etc/mpd.conf to configure it.

(You can still configure the *clients* at user level.)

---

### Post by NeonBible on 2009-01-19
Sounds good enough for me!

Have you by any chance checked out ncmpc++?

---

### Post by stefangr1 on 2009-01-19
> **NeonBible said:**
> Help me on my quest to go completely CLI and not use X at all!

This is not permanent.  I simply doing this for fun and to learn a bit more about CLI.



It might be a good idea to install vmware or virtual box on your computer, if you want to learn and play around. It emulates a virtual computer, which acts completely like a normal one, but there is no chance to mess up your normal system while you can can also try things that are a bit risky without having to worry.

---

### Post by adamlau on 2009-01-19
Regarding volume, alsamixer, or aumix. Recommended apps include htop, aria2, xorriso and Midnight Commander :) .

---

### Post by mcduck on 2009-01-19
> **NeonBible said:**
> Sounds good enough for me!

Have you by any chance checked out ncmpc++?

Looks nice, but I haven't tried it. I'm too lazy and have too little available disk space to bother with compiling programs.. ;)

---

### Post by NeonBible on 2009-01-19
Woah yeah, compiling is a nightmare but got ncmpc++ in the end.

Its good!! Better Library browser, shows song title in the window title.  Still need to check out the other features.

---

