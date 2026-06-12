---
title: "lirc, .lircrc config, dual monitor"
date: 2009-02-19
forum: General Help
---

### Post by lordofduct on 2009-02-19
Ok for starters I'm running two X screens right now.

That is two independent screens on which I can NOT drag stuff back and forth between the two, the monitors are two different sizes and resolutions so I can't stretch across nicely.

I use my main monitor for work, programming, and general stuff. Yes I'm slightly new to Unix.

My left monitor is for multimedia and minor things. It's where I open up Rhythmbox and Pidgin. If I want to watch a movie while working I put it on the left monitor. All that little stuff.

The thing is this also means that my remote control is usually controlling something on my left monitor as well. But it is used for MythTv on the main monitor (it's the larger of the two at 30 inches, yey TV).

[IMG]http://img.photobucket.com/albums/v333/lordofduct/MessBoard/triple01.jpg[/IMG]



SOOOOOO

my question.

I'm configuring lirc to open up and control rhythmbox.

my config file for test purposes looks like this so far:

```

#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa

##################
## <--IREXEC--> ##
##################

####start rhythmbox
begin
	remote = mceusb
	button = Home
	prog = irexec
	repeat = 0
	config = rhythmbox
end
##
# Rhythmbox key bindings.
##
begin
	remote = mceusb
	prog = rhythmbox
	button = Play
	repeat = 0
	config = play
end
begin
	remote = mceusb
	prog = rhythmbox
	button = Pause
	repeat = 0
	config = pause
end

```

Just a few basic commands.

The thing is it only starts rhythmbox on the main screen, and the play or pause commands only work IF rhythmbox is on the main screen. If I manually open it on the left one, and push buttons, rhythmbox never receives the commands.

What can I do to direct it over to the left screen????

---

### Post by lordofduct on 2009-02-19
i'm assuming it's something to do with what I type in the "config" command or something... err, not sure...

is there a way in a terminal window to select which screen a graphical app opens? I know the screen numbers of each X display.

---

### Post by nstenz on 2009-09-16
> **lordofduct said:**
> is there a way in a terminal window to select which screen a graphical app opens? I know the screen numbers of each X display.


It's a per-app option.  In the case of Rhythmbox, there is a --screen= option and a --display= option, depending on how you have your X server set up.

(A little late to the party, but I just saw the command line option in case anybody else runs across this topic. See *rhythmbox --help-gtk*)

---

