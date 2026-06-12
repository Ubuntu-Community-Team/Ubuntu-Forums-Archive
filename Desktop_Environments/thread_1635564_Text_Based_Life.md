---
title: "Text Based Life"
date: 2010-12-02
forum: Desktop Environments
---

### Post by Alpha101 on 2010-12-02
For some time I have been interested in life without a GUI, not necessarily living that life per-say but "interested" as a child would be about astronauts. So having taken said interest I've began to study it lightly at first, trying CMUS as my music player (A text based music player ran through terminal). I've also gotten a "Basic" (in the loosest of terms) understanding of how to import music through said program. Other than such, I know how to change directory, and see files via ls commands.

```
 
cd
ls
ls-a

```See that? Thats the entire list of commands I'd say I have a grasp on. Even...

```

Sudo apt-get install/purge

```...will sometimes elude me as to the full boundaries of it's uses; So I come asking this, amongst all of you does anyone live within a text based environment for extended periods? Days? Weeks? Years? 
Does anyone have advice on programs to use, on cool ways to learn, or even personal experiences they'd like to share?
What advantage does living a text based computer lifestyle give you against GUI folks?
What are the major bits of "expert" / "veteran" advice you'd give to new folks looking in to text interface?

:::if this seems to be the wrong sub-forum please move to whatever is deemed so.
Thank you for the time,

Austin

---

### Post by TiBaal89 on 2010-12-02
Browsing the web can be pretty fun... try playing with Lynx.  Better yet, trying responding to this thread using it! :D

[http://en.wikipedia.org/wiki/Lynx_%28web_browser%29](http://en.wikipedia.org/wiki/Lynx_%28web_browser%29)

---

### Post by Liverbones on 2010-12-02
> **TiBaal89 said:**
> Browsing the web can be pretty fun... try playing with Lynx.  Better yet, trying responding to this thread using it! :D

[http://en.wikipedia.org/wiki/Lynx_%28web_browser%29](http://en.wikipedia.org/wiki/Lynx_%28web_browser%29)

Really, I find ELinks easier to use, and it can be installed with [FONT="Monospace"]sudo apt-get install elinks[/FONT] rather easily. The interface is a bit daunting to use at first, but quickly becomes very natural.

There are quite a few other essential shell commands, probably the most useful of which is [FONT="Monospace"]man[/FONT], which can give you information about almost anything. It's truly wonderful. Simply type [FONT="Monospace"]man program_name[/FONT], and it'll give you as much information as is written in that program's man page. Really invaluable.

I also personally use a minimalistic window manager quite often; I used to be addicted to Openbox, then moved to ion3, and recently started trying wmii. But the greatest advantage of living on the command line for me would have to be the speed at which I find I can achieve tasks. You don't know how much faster using just a keyboard can be until you have done it enough to be perfectly comfortable. :)

There are also plenty of other things that I could tell you about, if you are interested, but I'm certainly no guru at the prompt. I simply know how to get around and do the things I need to do. :)

---

### Post by Girya on 2010-12-02
welcome aboard the terminal bus. you'll find that its much more adaptable to your prefs than a desktop.

 I do pretty much everything in a terminal except web browsing. here is a list of some of the apps i use: Music, cmus is awesome. Vim for text 
(checkout vigor, its vim with a the paperclip buddy from windows). Mutt for email. rsync for backups and a awk script for balancing my checkbook (the script is getting closer to being able to self reconcile my checking acct.), remind for appts. rcs for keeping archives of different versions of letters and scripts and configuration files. mplayer for watching dvds, mencoder for ripping dvds, grep sed and awk for searching and manipulating text. and nut-nutrition (build from source the one in the repos crashes alot) for keeping track of all the crap I eat. lpr for quick printing of files without opening them. 

my favorite trick is using the tab key for auto completion.

you've made a smart choice going to a terminal life.

---

### Post by Alpha101 on 2010-12-02
> **TiBaal89 said:**
> Browsing the web can be pretty fun... try playing with Lynx.  Better yet, trying responding to this thread using it! :D

[http://en.wikipedia.org/wiki/Lynx_%28web_browser%29]("http://en.wikipedia.org/wiki/Lynx_%28web_browser%29")

24 page installation manual...
I'm almost afraid.

> **Girya said:**
> welcome aboard the terminal bus. you'll find that its much more adaptable to your prefs than a desktop.

 I do pretty much everything in a terminal except web browsing. here is a  list of some of the apps i use: Music, cmus is awesome. Vim for text 
(checkout vigor, its vim with a the paperclip buddy from windows). Mutt  for email. rsync for backups and a awk script for balancing my checkbook  (the script is getting closer to being able to self reconcile my  checking acct.), remind for appts. rcs for keeping archives of different  versions of letters and scripts and configuration files. mplayer for  watching dvds, mencoder for ripping dvds, grep sed and awk for searching  and manipulating text. and nut-nutrition (build from source the one in  the repos crashes alot) for keeping track of all the crap I eat. lpr for  quick printing of files without opening them. 

my favorite trick is using the tab key for auto completion.

you've made a smart choice going to a terminal life.

I'll have to check these things out.
I'm guess you've gone non-gui for awhile now no?


Liverbones, by all means tell me of what you know of text based life, no information is too small.

---

### Post by marshag63 on 2010-12-02
Alpha101,

Are you interested in a live CD that is text based only with tutorials for beginners and lots of fun stuff to explore?

[http://inx.maincontent.net/](http://inx.maincontent.net/)

INX 1.17 or you could even try the Lucid version
[http://inx.maincontent.net/devel/unstable/](http://inx.maincontent.net/devel/unstable/)

I've learned lots and had fun learning what you can do at the command line.

MDG

---

### Post by nothingspecial on 2010-12-02
You need to just do it.

First, learn how to use byobu/screen. It`s like a window manager for the shell.

Then, find some apps that you like. I like to use elinks for general browsing and links2 -g if I want to see pictures (shopping, looking for a recipe)

Get your framebuffer setup so you can watch videos/view photos.

Make some aliases so you can do stuff in a couple of key strokes (and install gpm for console mouse support). eg If I want to listen to bbc radio 6music I just type r6

```
alias r6='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r6.asx < /dev/null &'
```or mount my servers backup drive, I just type mtv

```
alias mtv='sshfs -o idmap=user ns@192.168.1.11:/media/backup ~/tv'
```some apps I use

browsing - elinks, links2
music      - squeezeboxserver, squeezeslave, mplayer
video      -  mplayer
pictures  -   fbi
chat etc  -  irssi with bitlbee
alpine    - email

and many others.

But if you want to do it, you could do no better than read the master`s blog

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

[ATTACH]177184[/ATTACH]

---

### Post by Hippytaff on 2010-12-02
I've been following this thread because, like the op, I would love to live without X, at least on an old laptop I've got hanging around the house...very informative thread.
 
I especially like this
[[COLOR=#444444]http://kmandla.wordpress.com/[/COLOR]]("http://kmandla.wordpress.com/")
 nice link Nothingspecial - I'm a convert :-) (as soon as I work out what a framebuffer is and how to configure it :-) )

---

### Post by mrmylanman on 2010-12-02
I am semi familiar with the command line.  I can get tasks done and configure things, etc but I keep the GUI out of habit and I also like to use GIMP and Inkscape a lot for work and such so I keep Gnome around on my desktop.

I had an old Atom box, however and I used Ubuntu Server on it and configured Samba, DNS and DHCP using the command line exclusively.  I loved how lightweight the OS is without a GUI on top of it, since the Atom is no speed demon.

At work we use Fedora on our servers and I have to do a few menial tasks on them like swapping drives and using Bacula.  Nothing exciting.

I use adb some for my EVO 4G.

---

### Post by 12apennachi on 2010-12-02
I am reeaaalllyyy bored today, as I have off of school due to a snowday. Anyways, I was trying to learn more about the bash shell and stuff when I stumbled across this thread. I think this is a really cool idea and I think I am gonna try it. I just need to get some terminal-based software installed to get started. Thanks for the inspiration!

---

### Post by nothingspecial on 2010-12-02
> **Hippytaff said:**
> I've been following this thread because, like the op, I would love to live without X, at least on an old laptop I've got hanging around the house...very informative thread.
 
I especially like this
[[COLOR=#444444]http://kmandla.wordpress.com/[/COLOR]]("http://kmandla.wordpress.com/")
 nice link Nothingspecial - I'm a convert :-) (as soon as I work out what a framebuffer is and how to configure it :-) )

Do this```


sudo usermod -a -G video username
```
This will allow you to use the framebuffer as a normal user (without sudo). Change username for your username.

Then 

Ctrl Alt F1 to get to the console

Then ```
mplayer -vo fbdev /path/to/video
```To alias it
```

echo 'alias vid="mplayer -vo fbdev"' | tee -a ~/.bashrc
``````

. ~/.bashrc
```From now on, just 
```

vid /path/to/video
```You can make it fullscreen with the zoom option and your resolution.

---

### Post by 12apennachi on 2010-12-02
I am replying to this message with elinks. This CLI stuff is pretty sweet. It is a little wierd not having a mouse and having to scroll through everything with the up/down buttons but it's fun.

---

### Post by nothingspecial on 2010-12-02
> **12apennachi said:**
> I am replying to this message with elinks. This CLI stuff is pretty sweet. It is a little wierd not having a mouse and having to scroll through everything with the up/down buttons but it's fun.

Press . (the full stop/period key)

Now, each link has a number infront of it.

Type that number and go to the link :D

See, you can even do smileys ;)

---

### Post by nothingspecial on 2010-12-02
> **12apennachi said:**
> I am replying to this message with elinks. This CLI stuff is pretty sweet. It is a little wierd not having a mouse and having to scroll through everything with the up/down buttons but it's fun.

or install gpm and click it ;)

---

### Post by nothingspecial on 2010-12-02
> **12apennachi said:**
> It is a little wierd not having a mouse and having to scroll through everything with the up/down buttons but it's fun.

Sorry for 3 replies one after another......

......it`s just that things keep occuring to me.

The up and down arrows in elinks navigate links (the things, in firefox, you can click on)

Try Insert and Delete........

........ or B and Space

;)

---

### Post by Hippytaff on 2010-12-02
Does elinks work with wireless?
Can't get it to go to a url...keeps saying file not found in hippyttaff/home//http etcetc

It's ok I got it...leave out the [http://www](http://www) - bit - sorry for butting in :-)

---

### Post by Liverbones on 2010-12-02
Well, both elinks and w3m are fantastic as web browsers for a CLI environment. If you use IRC, then you really can't go wrong with irssi, and for IM, there's always centerim (which has worked better for me than finch, which is essentially Pidgin for the console). I've always liked moc for music on the console, but that's really a personal preference, and there must be 10,000 different music players you can use at the command line. :P

But really, there are all kinds of useful applications for the command line. There's also wicd-curses for network management (as opposed to GNOME's NetworkManager), which I made heavy use of back in my ion3 days (oh Tuomo, why did you have to go insane?), and might start using it again if I'm feeling a bit lightweight. :)

There's also rtorrent for managing torrents from the terminal, but you'll definitely want to read the man page for it; the keyboard shortcuts for that program are a bit bizarre in my opinion. There's also hnb, hierarchical notebook, which you can use similarly to how you might use something like Tomboy Notes (I used it excessively :P), and you can always use nano for text editing.

Now, nano and w3m are included by default in Ubuntu, so you don't need to install anything to use them. Simply invoke the commands (although w3m won't do much without a URL to go to, so you might use [FONT="Monospace"]w3m google.com[/FONT] to get started).

So, if you want to install any of these, you can just [FONT="Monospace"]sudo apt-get install[/FONT] any of them as named. If you wanted everything, you could just [FONT="Monospace"]sudo apt-get install centerim elinks hnb irssi moc rtorrent wicd-curses[/FONT] and you're good to go. Just keep in mind that the wicd-curses packages will remove some standard parts of your Ubuntu distribution (GNOME's NetworkManager, which might not be such a bad thing). If you're feeling brave, give it a go; if not, just don't use it yet. :)

But there are also tons of other command line applications and utilities that I could recommend if you're trying to do anything particular at the command line. These are just a few things to get you started on using the command line on a day-to-day basis. :)

---

### Post by TiBaal89 on 2010-12-02
ok, elinks is the greatest thing ever... i discovered it accidentally, but i love the functionality of the '.' key - where it numbers all the links on the page.  you can just tpye the number in out of the blue and go to that link.  very handy way to surf pages with tons of links without using the mouse. 

the only problem i'm seeing right now is that when i enable colors, it makes the background color something really tough to look at (i.e. white).  i'll have to look into that more...

---

### Post by Liverbones on 2010-12-02
> **TiBaal89 said:**
> ok, elinks is the greatest thing ever... i discovered it accidentally, but i love the functionality of the '.' key - where it numbers all the links on the page.  you can just tpye the number in out of the blue and go to that link.  very handy way to surf pages with tons of links without using the mouse. 

the only problem i'm seeing right now is that when i enable colors, it makes the background color something really tough to look at (i.e. white).  i'll have to look into that more...

You can customize all of the colors from the ELinks menu. Just hit Escape, then select Setup > Options Manager (or use Escape, then S, then O on the keyboard if you're feeling snappy :P). Within the Options Manager, go to User Interface, then Color Settings, and finally Color Terminals. Once there, you can select the color for any part of the ELinks UI and change it.

---

### Post by TiBaal89 on 2010-12-02
> **Liverbones said:**
> You can customize all of the colors from the ELinks menu. Just hit Escape, then select Setup > Options Manager (or use Escape, then S, then O on the keyboard if you're feeling snappy :P). Within the Options Manager, go to User Interface, then Color Settings, and finally Color Terminals. Once there, you can select the color for any part of the ELinks UI and change it.

Thanks, I did see that... it seems like those color settings are for the elinks elements themselves.  I'm referring to the rendering of the page - i.e. link colors, page background, etc.  Unless I missed that...

---

### Post by marshag63 on 2010-12-02
Here's something fun - get the INX live CD 1.17 version, boot it up and watch the short movie "A New Computer" -- it blew my mind that I could watch a video in framebuffer (everything is set up perfectly for it).

I like to boot up INX, fire up a shoutcast channel I like and then hit the IRC channels while I surf in Elinks or check gmail.  (BTW, the "search for shoutcast streams" is broke, but if you choose the "radio" option and pick a link from the shoutcast webpage it loads in elinks, it will open and play very nice indeed).

INX even has a wifi client called CENI, which supports my Belkin USB adapter out of the box (YAY!).  Just a tip, if you are booting INX on a netbook, you need to use either F5 or F6 at the grub boot to change the screen size or it all will not fit on the screen and you will have unreachable options.

Great tip about pressing "." in elinks to turn on link navigation -- first thing I do.  You can also have multiple tabs and jump amongst them.
Esc key brings up the menu and also removes it.

Screen is a great little app - it little weird to get used to at first, but mighty handy once you get the hang of it.

Love, love, love moc!

CLI can rock!

MDG

---

### Post by Liverbones on 2010-12-02
> **TiBaal89 said:**
> Thanks, I did see that... it seems like those color settings are for the elinks elements themselves.  I'm referring to the rendering of the page - i.e. link colors, page background, etc.  Unless I missed that...

As far as I know, that's controlled by the page, not ELinks, just like any other web browser. The Google page's background is white because Google wants it to be white. :)

But you can define an external stylesheet for ELinks to use. Create your stylesheet, then place it in ~/.elinks. Then open ELinks, go to Setup > Options Manager > Document > Cascading Style Sheets > Default Stylesheet and just type in the name of your stylesheet (without the rest of the path).

I believe that should do what you're wanting. :)

---

### Post by TiBaal89 on 2010-12-02
Yes!  I will certainly do this... flippin awesome.  Thanks. :D

---

### Post by Alpha101 on 2010-12-03
Responding via elinks, cant seem to get it to scroll down persay
Edit- This..Just plain rocks, but is wonky to use.
For some reason when I enter in the link number it takes me to thr wrong one, odd for some reason.
I'll figure it out sooner or later. But this is *Nice*!

---

### Post by Alpha101 on 2010-12-03
> **Alpha101 said:**
> Responding via elinks, cant seem to get it to scroll down persay
Edit- This..Just plain rocks, but is wonky to use.
For some reason when I enter in the link number it takes me to thr wrong one, odd for some reason.
I'll figure it out sooner or later. But this is *Nice*!

This does it for me.
I dont need video, I dont watch stuff, but if I did I know where to look for programs.
I want to be able to boot an OS off a flash drive, with no GUI(Or so literally basic that it makes minimalists cry in happiness), black screen and lime green text only, 
Fast, and -small-.
Whats the best shot mates?
I sound mad or like I'm trying to be a poser with the green text reference to matrix, but heck it's easy to read.

---

### Post by Alpha101 on 2010-12-03
> **marshag63 said:**
>  INX
Downloading right now...sadly through gui, and then going to try running it in a VM.

---

### Post by nothingspecial on 2010-12-03
In elinks, go to the link then hit D to download.

---

### Post by marshag63 on 2010-12-03
Alpha101, INX has the matrix screensaver and green text in most apps.

In Elinks, use Insert/Delete to scroll up/down.  When you jump to a link to enter text, press the Enter key first and it will let you type your text.

Good news, INX can be put on a USB key (if you want persistence -meaning you want to keep any settings you change, that is possible to do - I'm not sure where to find those instructions again).

If you do run INX, don't forget to run through the tutorials.  Also, fire up irssi and pop in the INX chat room - they are great people, but it tends to be one of those quiet channels.

MDG

---

### Post by Hippytaff on 2010-12-03
I had a bash at INX yesterday from liveCD - excellent!
 
However, when I reboot it won't boot into ubuntu, just a black screen, no blinking curser - nada - so I have to do a hard shutdown and boot. then everything is fine...This is not going to stop me using it, just posting to see if anyone else has experienced this?
 
Also - When trying to acces facebook from elinks it replies 'sorry, facebook is not cool enough to support your broswer, try firefox, Chromium etc'
 
Not bothered about this either, but thought I'd share that - give it a go just for the fun of it :-)

---

### Post by 12apennachi on 2010-12-03
Does anyone know how to change the text colors in a tty? I know it sounds dumb but I want the green text like in those old 80s hacker movies, (born in '94). Anyways if anyone could tell me how to do that I would really apppreiciate it. Also, I am doing everything on here, from browsing with elinks to downloading movies with transmissioncli and watching them with mplayer. Which reminds me, I can't get sound out of mplayer, I have mute: disabled, and I press zero and it says "volume 100%" and I even used alsamixer to increase the voolume but nothing. Even when I am just playing mp3's. How do I get sound?  P.S Hipptaff, I can't go on facebook either, but thats okay, I am on a cli and nobody cares what I have to say anyways.

Edit: I got the green text with setterm -foreground green

---

### Post by 12apennachi on 2010-12-03
[QUOTE=12apennachi;10193999]Does anyone know how to change the text colors in a tty? I know it sounds dumb but I want the green text like in those old 80s hacker movies, (born in '94).[\QUOTE] Sorry for the double post but elinks is being wierd and won't let me edit the post. Anyways I got the green text with setterm -foreground green

---

### Post by nothingspecial on 2010-12-03
Put this in your .bashrc

```
setterm -foreground green -background black -store
```

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> Put this in your .bashrc

```
setterm -foreground green -background black -store
```

Sorry I am a noob, but where is .bashrc?
Nevermind I found it.

---

### Post by nothingspecial on 2010-12-03
It in your home

```
nano ~/.bashrc
```Put the setterm line at the end.

Press Ctrl - O then Enter to save

Then Ctrl - X to exit nano

Then type

```
exit
```Then log back in.

You`ll need to nano .bashrc to make some aliases.

Try putting this line in
```

alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```Then type ,```
. ~/.bashrc
```To get it to read your .bashrc again

Then just type ```
punk
```I have loads of aliases. Don`t worry about editing your .bashrc, there is a copy of the default one in /etc/skel

I manage my ipod in the console, but that really would be a pain without aliases. So think of some of your own.

---

### Post by nothingspecial on 2010-12-03
:twisted: I suppose I ought to tell you how to switch it off

:-\"

Ok ```
killall mplayer
``` is the quickest.

(you can alias that too)

Sorry, that one I posted might be a nightmare if you don`t like punk.

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> :twisted: I suppose I ought to tell you how to switch it off

:-\"

Ok ```
killall mplayer
``` is the quickest.

(you can alias that too)

Sorry, that one I posted might be a nightmare if you don`t like punk.

Thanks for the help, unfortunately I figured it out(the green text thing) by accidentally deleting a line in vim, I was crapping my pants. But I got it straightened out with nano. But what you said about alias', what do they do? Is it just a copy of the bashrc file or something? I am a little confused. Or is it like a shortcut for a command? Ok nevermind, maybe I do get it.

---

### Post by nothingspecial on 2010-12-03
I have some really long commands that I like to do often. I couldn`t tell you them off the top of my head.

An alias is a little short hand you can make any command. You put it in your .bashrc

(you can have a seperate file for them called .bash_aliases, but lets keep this simple)

I`ll show you a few of mine
```

alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f) < /dev/null &'
```That plays my music collection on random, in the background (not really quiet, I mean it gives me the prompt back)

All I have to type is```
 ran
```

I don`t have to remember the really long command.

Here is another one that will rip a cd to flac files
```

alias cd2flac='abcde -c ~/.abcde_flac.conf'
```all I have to do is type ```
cd2flac
```(You do need abcde and an appropriate config file aswell)

So, if you want to try living in the console for a while, you`re going to love aliases.

The first alias I showed you plays a punk radio stream, again in the back ground.

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> I have some really long commands that I like to do often. I couldn`t tell you them off the top of my head.

An alias is a little short hand you can make any command. You put it in your .bashrc

(you can have a seperate file for them called .bash_aliases, but lets keep this simple)

I`ll show you a few of mine
```

alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f) < /dev/null &'
```That plays my music collection on random, in the background (not really quiet, I mean it gives me the prompt back)

All I have to type is```
 ran
```

I don`t have to remember the really long command.

Here is another one that will rip a cd to flac files
```

alias cd2flac='abcde -c ~/.abcde_flac.conf'
```all I have to do is type ```
cd2flac
```(You do need abcde and an appropriate config file aswell)

So, if you want to try living in the console for a while, you`re going to love aliases.

The first alias I showed you plays a punk radio stream, again in the back ground.

Thank you so much, you have tought me more helpful things today than I have learned in a long time. I am loving this stuff. And just about everytime I mess around with something that you tell me to do I edit my reply saying nevermind but then you post back with some nice explanation haha. Thanks again.

---

### Post by nothingspecial on 2010-12-03
No problem.

You must read kmandla`s blog I linked in the first page of this thread.

He has instructions on setting up loads of cli stuff.

---

### Post by 12apennachi on 2010-12-03
Did you try to send me through to your ip through port 8600? Is that where your music is? It didn't let me through. Anyways, that is irrelevant, but my real question is, how do I get my sound to play? I have alsamixer volume all the way up as well as mplayers volume at 100%, with mute disabled, I have tried everything I know but this is beyond my knowledge I am sure. Any ideas?

---

### Post by nothingspecial on 2010-12-03
No it`s a shoutcast radio stream.

As for the volume, are you using full blown ubuntu (just using the console), minimal ubuntu or inx? 

This threads getting long.

---

### Post by nothingspecial on 2010-12-03
And has it ever worked?

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> And has it ever worked?

It always worked with a gui, but I never got it to work in just a straight up tty. I basically have a whole gnome desktop but instead of logging in there I log into ttyx. I don't know if that helps any. Also, I am running 10.04.1.

---

### Post by nothingspecial on 2010-12-03
That is very strange???

You sure everything is unmuted in alsamixer.

Also, I know you`re trying not to but does it work if you log in to gnome then go back to tty1

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> That is very strange???

You sure everything is unmuted in alsamixer.

Also, I know you`re trying not to but does it work if you log in to gnome then go back to tty1

Wierd, it works after I log in and out of gnome. But I would rather not have to do that. If you can't figure it our I understand. But what do you think?

Edit: I just restarted and it suddenly works now. But it's wierd because I restarted multiple times yesterday and it still failed. Maybe because I didn't use audio in gnome since I started using cli until now. I don't know. Either way it is fixed so thank you sooooo much for all of your help. I think that is all I need..... Hopefully.

---

### Post by nothingspecial on 2010-12-03
I just tried doing that myself on the main family pc.

I logged straight in to tty and the sound was off in alsamixer, but I was able to turn it up.

Strange, anyway I see it`s fixed now :D

---

### Post by nothingspecial on 2010-12-03
@12appennachi

The first app you need to become familiar with is screen.

It`s like a desktop environment for the shell. It allows you to have different "tabs" and/or "windows" in the same tty.

Look at the screenshot ......

[ATTACH]177304[/ATTACH]

Can you see, I have 4 windows?

On the right, I have elinks

Top left, I have my music player.

Underneath that I have my IRC chat client. (The middle window, is for messages (which I have cleared for the sake of privacy))

This program, screen, really does bring using the cli into it`s own.

At the bottom of the screenshot you can see the notification panel. I have a battery monitor, a network analyser, a clock etc etc.

I also have a "window list" under every window.

I have this setup to launch like this, but I`m just going to give you a few basics here. The web will guide you further.

So, in a tty, type

```
byobu
```

This launches ubuntus funked up version of screen - with the notification panel.

You have a prompt, like any terminal.

Launch elinks. Ok, but what if you want to do something else, like cmus for example?

No problem.

Press F2

and you will get a new window. Launch cmus and start some music.

Now you want to go back to browsing........ ok, press F3

back to music - F4

back to browsing - F3

So, F2 launches a new "session", and F3 and F4 move between them left and right.

That is the basics of having different windows on the same tty.

Note ...... framebuffer apps don`t like screen. If you want to watch a video, view an image or use links2 -g you will have to use a different tty.

Cheers :D

---

### Post by TiBaal89 on 2010-12-03
oh man, this is fun... i just wish i'd start playing with this stuff a week other than the last one of the semester ;)

currently listening to shell-fm... it has features that the graphical last.fm player doesn't have for any system, as far as i'm aware.  being able to pause is a major one, i always found it annoying that there is only a play and stop button on the last.fm player.  not so here!  some other cool stuff as well... very nice.

what's a good way to open a bookmark in a new tab in elinks?  when you open a new tab with 't' it deafults to asking you to type a URL and i don't see something like 'open in new tab' in the bookmark manager dialog.  hmmm...

EDIT:  nevermind that last bit... looks like 't' opens the new tab as a duplicate of where you are, and you can just <Esc> out of the dialog and hit 's' to bring up the bookmarks.  not one key, but not bad...

---

### Post by 12apennachi on 2010-12-03
> **nothingspecial said:**
> @12appennachi

The first app you need to become familiar with is screen.

It`s like a desktop environment for the shell. It allows you to have different "tabs" and/or "windows" in the same tty.

Look at the screenshot ......

[ATTACH]177304[/ATTACH]

Can you see, I have 4 windows?

On the right, I have elinks

Top left, I have my music player.

Underneath that I have my IRC chat client. (The middle window, is for messages (which I have cleared for the sake of privacy))

This program, screen, really does bring using the cli into it`s own.

At the bottom of the screenshot you can see the notification panel. I have a battery monitor, a network analyser, a clock etc etc.

I also have a "window list" under every window.

I have this setup to launch like this, but I`m just going to give you a few basics here. The web will guide you further.

So, in a tty, type

```
byobu
```

This launches ubuntus funked up version of screen - with the notification panel.

You have a prompt, like any terminal.

Launch elinks. Ok, but what if you want to do something else, like cmus for example?

No problem.

Press F2

and you will get a new window. Launch cmus and start some music.

Now you want to go back to browsing........ ok, press F3

back to music - F4

back to browsing - F3

So, F2 launches a new "session", and F3 and F4 move between them left and right.

That is the basics of having different windows on the same tty.

Note ...... framebuffer apps don`t like screen. If you want to watch a video, view an image or use links2 -g you will have to use a different tty.

Cheers :D

Thanks alot man that's really cool. I have been using this pretty much all day (didn't move from my chair) and I have learned soo much and have become much more confortable with bash. this screen thing is an awesome program

---

### Post by K.Mandla on 2010-12-04
Am I too late for the party?

[[img]http://ompldr.org/tNmY3NQ[/img]](http://ompldr.org/vNmY3NQ)

That's a few months old, but not unusual for me. :)

---

### Post by nothingspecial on 2010-12-04
^
                                                                   |


Ah the master returns. I learned all I know from him. Again, read his blog. Set up alpine, rtorrent, elinks etc.......it`s all there. :P

Actually, I got alot of good stuff from andrew as well. In particular his abcde set ups I mentioned earlier. See below

[http://www.andrews-corner.org/index.html](http://www.andrews-corner.org/index.html)

---

### Post by Hippytaff on 2010-12-04
Feel like we've been visited by a guru - Excellent blog Sir Mandla :-)

---

### Post by 12apennachi on 2010-12-04
I need a picture viewing program, and I have tried opening a png with vgz or zgv.. whatever, it gave me a mouse error, I changed the /etc/vga/something.comfig to mouse none, and i get a flat cursor, and when I go to ttyx, I can't go back to the tty where zgv is, it won't let me, so I have to kill the process. I also tried aview and feh, though I now realize feh is for X, correct? Anyways, can I open png's in a tty? and if not what formats can I open and with what programs. And I did not use them in a screen, as I have heard that doesn't work either. btw,I also tried asciiview, supposed to convert the file to pgm and then open with aview but it didn't work either, I just got a bunch of numbers and crap on my screen(maybe supposed to be the picture?)  Any ideas?

---

### Post by nothingspecial on 2010-12-04
fbi is the app you want to display images in the fb

You are right that it wont work in screen.

---

### Post by 12apennachi on 2010-12-04
> **nothingspecial said:**
> fbi is the app you want to display images in the fb

You are right that it wont work in screen.

Thank you very much, works perfectly.

---

### Post by nothingspecial on 2010-12-04
> **12apennachi said:**
> Thank you very much, works perfectly. And another question. When I am using elinks it will not reload a page after I click on the link to the page I am on, it just shows what I have. i.e. If I am an ubuntuforums page 6, I either click on page 6 link or "reload this page" but it doesn't reload, it tries to take a shortcut and just show me what it already has. I have to restart elinks everytime I want to update the forums.

Ctrl R

to refresh.

btw, for viewing images in ASCII, jp2a is fun. The correct commands can be quite long but then we have aliases don`t we ;)

[ATTACH]177385[/ATTACH]

Oh, you need imagemagick for using jp2a with pngs

To do that I had to do
```

convert big\ tux.png jpg:- | jp2a - --colors --background=dark -z
```

---

### Post by mr.farenheit on 2010-12-04
i miss running BASIC as an OS

---

### Post by K.Mandla on 2010-12-04
> **nothingspecial said:**
> Ah the master returns. ...

> **Hippytaff said:**
> Feel like we've been visited by a guru - Excellent blog Sir Mandla :-) ...
You are all too kind. I am humbled. :)
> **nothingspecial said:**
> Ctrl R ... to refresh.
You can also map keys in elinks; I find CTRL+R counterintuitive, so F5 works on mine too.
> **nothingspecial said:**
> btw, for viewing images in ASCII, jp2a is fun. The correct commands can be quite long but then we have aliases don`t we ;)
You can also look into the aalib and cacalib libraries; if I remember right, they both have functions to convert images into textified renditions. :)

The caca libraries are particularly fun; they come with a few "screensavers," of rolling, shifting color patterns. You might have to recompile them to get those though. I don't know of the Ubuntu package maintainers kept those in their versions.

Next step is to wire those into screen's blanker setting and make yourself a few timed "screensavers" for fun. :)

---

### Post by Hippytaff on 2010-12-04
I seem to be having trouble with elinks and google. No results appear when searching...reinstalled it but no luck. Am I right in thinking you type the keyword and enter? or am I missing something exceptionally obvious :-s

I also tried going to the 'search' link, nothing...ergh?

---

### Post by sisco311 on 2010-12-04
was going to post a link to K.Mandla's blog... too late...  

anyway, here is another useful link for beginners:

[thread=882596]HOWTO: Ubuntu CLI versions & Framebuffer Programs[/thread]


> **nothingspecial said:**
> 
```

alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```

Thanks! Cool!


~soupy twist!

---

### Post by nothingspecial on 2010-12-04
Now I`m embarrassed.....:oops:

I forgot sisco #-o

He doesn`t have a blog afaik, but just using the forums and reading his (far better than mine) answers has taught me so much about using linux - bash specifically in sisco`s case.

Yes sisco311, I`ve nicked (stole) loads of funky commands from you :P

  	12apennachi, Hippytaff ........ you have been visited by 2 gurus. :D

---

### Post by nothingspecial on 2010-12-04
> **K.Mandla said:**
> You are all too kind. I am humbled. :)

You can also map keys in elinks; I find CTRL+R counterintuitive, so F5 works on mine too.

You can also look into the aalib and cacalib libraries; if I remember right, they both have functions to convert images into textified renditions. :)

The caca libraries are particularly fun; they come with a few "screensavers," of rolling, shifting color patterns. You might have to recompile them to get those though. I don't know of the Ubuntu package maintainers kept those in their versions.

Next step is to wire those into screen's blanker setting and make yourself a few timed "screensavers" for fun. :)

See ........ told ya :P

---

### Post by nothingspecial on 2010-12-04
> **Hippytaff said:**
> I seem to be having trouble with elinks and google. No results appear when searching...reinstalled it but no luck. Am I right in thinking you type the keyword and enter? or am I missing something exceptionally obvious :-s

I also tried going to the 'search' link, nothing...ergh?

If it weren`t for this (and the numbered links................. and the cookies), I would use links2.

So, to get to a search box, press G

You can type a url in there and it will go.



....but.... elinks has built in search engines ;)

Press G to open the search box again. Then press G again, then space, then your search term - eg ubuntu .....

.... so it looks like this in the search box

```
g ubuntu
```

That will search google for the following term, in this case ubuntu.

Now try pressing G

then

```
wiki ubuntu
```

Do you see where I`m going here?

There are other inbuilt searches in elinks ;)

---

### Post by 12apennachi on 2010-12-04
^^That is an awesome feature of elinks. The CLI just gets better and better as I continue to read this thread... I am actually considering doing a server install, the gui truly does slow things down, and I don't mean physically taking up more cpu power and ram, I mean using the mouse in chromium vs typing ". 13 <enter>" in elinks. And the alias feature is awesome, instead of going to rhythmbox  and hitting play, I type "music" and my mplayer starts shufflin' my music folder. I know I say alot but i feel the need to tell someone, I don't know anyone who understands. So I have movies fullscreen, pictures, music, mutt email, elinks, I changed pennachi@pennachi-laptop ~:$ to pennachi <time> ~:> with colors, thought it was cool. I have byobu down, I have BSDgames, vitetris, moon-buggy. Any other cool programs? Fun or useful, both are entertaining for me.

---

### Post by Alpha101 on 2010-12-05
nothingspecial:
A text based fountain of information.
I've been using INX, Elinks, mplayer, and some of the basics of the tut's I've gotten from INX.
I dont know why I ever invested so much money into this damn PC anymore..
This is amazing.

Holy snikeys, K. Mandla was here?
I've been eating up every single blog post of theirs for weeks now.
Jesus man I didnt think it'd be this popular!

---

### Post by TiBaal89 on 2010-12-05
just lost my gnu screen detach virginity... my mind is blown.

---

### Post by Hippytaff on 2010-12-05
> **nothingspecial said:**
> If it weren`t for this (and the numbered links................. and the cookies), I would use links2.

So, to get to a search box, press G

You can type a url in there and it will go.



....but.... elinks has built in search engines ;)

Press G to open the search box again. Then press G again, then space, then your search term - eg ubuntu .....

.... so it looks like this in the search box

```
g ubuntu
```That will search google for the following term, in this case ubuntu.

Now try pressing G

then

```
wiki ubuntu
```Do you see where I`m going here?

There are other inbuilt searches in elinks ;)

that is immense...cheers

---

### Post by Hippytaff on 2010-12-05
Need a little assistance with screen now...I can split no problems, but only one section can run anything in, so I'm defo missing something obvious again. :-s

---

### Post by nothingspecial on 2010-12-05
To move to a new section press Ctrl -A then Tab

When you first split, there is no pronpt in the new window. If using byobu press F4 to get to an existing window or F2 to create a new one.

(Ctrl -A C and Ctrl-A number in regular screen)

I find it usefull to name "windows"

In byobu press F8 to name your window.

---

### Post by nothingspecial on 2010-12-05
byobu has been making me lazy :)

Just thought, another way of switching windows is Ctrl-A then " (Shift-2)

That will present you with a list of all your windows which you can navigate with your arrow keys and select.

Out to lunch....... have fun:p

---

### Post by Hippytaff on 2010-12-05
Thanks byobu is much easier :-)

Now if I could get the kids to play with their toy's quietly for the rest of the day, I could play with my toy :-)

---

### Post by wojox on 2010-12-05
> **Hippytaff said:**
> Need a little assistance with screen now...I can split no problems, but only one section can run anything in, so I'm defo missing something obvious again. :-s

You need [Screen User's Manual]("http://www.gnu.org/software/screen/manual/html_node/index.html#Top")

Also install [Irssi]("http://www.irssi.org/documentation")

Great IRC client.

---

### Post by Hippytaff on 2010-12-05
Is there a conky for cli? and also a clock :-)

---

### Post by gutterslob on 2010-12-05
> **Hippytaff said:**
> Is there a conky for cli? and also a clock :-)
You can always configure your current conky to output itself to the console.
just add the line;
```
out_to_console yes

```to your conkyrc. You can adjust the update interval as you like. Then just type "conky" in your tty (press Ctrl+C to stop it) 

BUT......

Personally, I'd recommend dstat instead of conky if you want some sort of system monitor for the console, or better yet, configure Screen to show system stats (someone already linked the Screen manual in a prior post on this thread, iirc)

There's also Byobu, which is sort of a preconfigured/readymade screen setup (just install it from your repos and launch it in a tty)

As for the clock, conky or screen/byobu should have that, or you can install tty-clock
[https://github.com/xorg62/tty-clock](https://github.com/xorg62/tty-clock)
Make sure you have a curses library and runtime environment before you run make.
On debian, the packages are libncurses5-dev, ncurses-base and ncurses-term , so I assume they should be the same for ubuntu.

Other apps that might interest you are slurm (network traffic) and ttyload .Both are unnecessary if you have screen/byobu already showing your stats, though.

---

### Post by Hippytaff on 2010-12-05
thanks gutterslob
I'm using byobu rather than screen (found screen a bit difficult at the moment - only just getting into cli eventhough I've wanted to for years)
I'm using htop right now. will try dstat...

thankyou :-)

---

### Post by 12apennachi on 2010-12-05
> **Hippytaff said:**
> Is there a conky for cli? and also a clock :-)

As for the clock, I edited my PS1 in bash rc to look like this:

```
PS1='\e[0;32m\]\u\[\e[m\] \[\e[0;31m\]\T\]\e[m\] \[\e[1;34m\]\w\]\e[m\] \[\e[1;32m\]$\[\e[m\] \[\e[1;32m\]'
```

This makes it user(green) <time>(red) <pwd>(blue) and $(lightgreen) and as for the last \[\e[1;32m\], it has no end, so any text typed after it is bright green. Anyways, if you wanted time              \[\e[0;31m\]\T\]\e[m\] That is it, If you don't want color just do \T,
 pennachi 05:00:39 ~ $
EDIT: I had problems with the PS1 setup above when using my terminal so I changed it to this:
```
PS1='${debian_chroot:+($debian_chroot)}\[\e[01;32m\]\u \[\033[00;34m\]\T\[\033[00m\]\[\033[00;31m\]:\[\033[01;31m\]\w\$\[\033[00m\]\[\033[01;34m\] '
```

---

### Post by Hippytaff on 2010-12-05
Excellent...your obviously far more advanced than me in this but as soon as I work it out I'll try it (are you using regular expressions there? my god man...my brain hurts :-) )

---

### Post by sisco311 on 2010-12-05
> **Hippytaff said:**
> (are you using regular expressions there? my god man...my brain hurts :-) )

Color escape sequences & prompt escapes.

I think, the Arch wiki explains them quite well:
 [https://wiki.archlinux.org/index.php/Color_Bash_Prompt](https://wiki.archlinux.org/index.php/Color_Bash_Prompt)

---

### Post by 12apennachi on 2010-12-06
> **Hippytaff said:**
> Excellent...your obviously far more advanced than me in this but as soon as I work it out I'll try it (are you using regular expressions there? my god man...my brain hurts :-) )
If you are talking to me I really am pretty noobish at this stuff, Everything I know I learned from these forums or other websites, and you have helped me out on multiple occasions. But I am getting a book so I can hopefully learn what I am doing on this thing.

---

### Post by Alpha101 on 2010-12-08
EDIT-
Elinks seems to auto log me out when I try to post.
I try to log in but it gives me an infinite loop of the same log in screen. I cant reply via elinks, and quick reply wont take my text. 
I'm runnin 10.10 Maverick and cmus in a terminal tab while elinks is going.

---

### Post by Hippytaff on 2010-12-08
> **Alpha101 said:**
> EDIT-
Elinks seems to auto log me out when I try to post.
I try to log in but it gives me an infinite loop of the same log in screen. I cant reply via elinks, and quick reply wont take my text. 
I'm runnin 10.10 Maverick and cmus in a terminal tab while elinks is going.

I've found this with elinks too...log in, then go to a random thread and then your suddenly signed in and you should be able to go to your CP...I don't know why this happens but that is the only workaround I've found..odd...don't get it with links2 :-s

---

### Post by sisco311 on 2010-12-08
Yep... [thread]1365734[/thread]

I prefer links2 with framebuffer support. Is that cheating?

---

### Post by Hippytaff on 2010-12-08
> **sisco311 said:**
> Yep... [thread]1365734[/thread]

I prefer links2 with framebuffer support. Is that cheating?
Nope..not cheating, I can't get framebuffer working though, so elinks is easier with the . link number toggle option (I'm not sure that made any sense :-s )

you know what I mean

---

### Post by nothingspecial on 2010-12-09
> **Hippytaff said:**
>  I can't get framebuffer working though

You need to add your self to the video group

```
sudo usermod -a -G video hippytaff
```
Also note that the framebuffer doesn't work within screen/byobu

So I have screen on tty1 including elinks.

links2 on tty2

and use tty 3 for videos, pictures etc

```
links2 -g -driver fb
```

So for lightening quick browsing with the . (;)) and the inbuilt search engines elinks 90% of the time.

links2 for shopping, recipes etc when you want to see the pictures.

..... elinks is useful within screen for copying and pasting links to/from irssi

---

### Post by Hippytaff on 2010-12-09
> 
Also note that the framebuffer doesn't work within screen/byobu

That's where I'm going wrong...I like the cli set up you discribe, I've just been using tty1 with byobu/screen splitting it thus elinks at the top section -  
Bottom section - irssi, teminal - for mutt and other just messing around with config files etc and tty-clock above htop. Just wanted to share my set-up. I'll try the frame buffer in a byobu-less tty2 tonight before I completely destroy my system trying do dual boot debain squeeze and ubuntu :-D

---

### Post by Sylos on 2010-12-09
Having read some of the posts on here Im now thinking of leaping into this as well. I have an old laptop that is useless for anything else (only 64mb of RAM so I've only managed to install Puppy linux on it so far). 

Does anyone know the minimum system requirements for a CLI only install of 10.04?

---

### Post by Hippytaff on 2010-12-09
> 
Does anyone know the minimum system requirements for a CLI only install of 10.04?

 
not sure exactly, but not much. there are other light distros too [http://distrowatch.com/](http://distrowatch.com/)
crunchbang looks good :-)

---

### Post by nothingspecial on 2010-12-09
Another option for splitting your screen is dvtm

It works a bit like screen in that you use an escape sequence to send it a command.

In screen it is Ctrl-A

In dvtm it is Ctrl-G

so install dvtm, then launch it
 
Press Ctrl-G then C to split

Do that  twice more so you have 4 windows

Then press Ctrl-G then G and you will get a nice grid.

Switch between them using Ctrl-G then J or K to go back and forth.

The thing about dvtm is that unlike splitting with screen, you can run a different screen session in each of dvtms windows. So you can have multiple screen sessions in different windows.

Note, you have to use screen rather that byobu - there is only one byobu.

You can even split each "screen" in each of byobu`s windows.

So with 6 ttys all running dvtm split into four with a screen in each running 6 seperate sessions..........

....... that`s 144 things you can do at once in the foreground :D

Actually it`s complete madness and you`ll just end up rebooting your server by mistake because you`ve lost track of where you are and what your doing.

Anyway, just thought I`d share ;)

---

### Post by Hippytaff on 2010-12-09
Excellent, another thing to play with, though it would definitely be madness for me to have more than 6 things going on at once, when that happens my brain melts and tries to escape out of my ears. :-)

---

### Post by nothingspecial on 2010-12-09
(Hastily put together) Screenshot so you can see what I mean

[ATTACH]177902[/ATTACH]

---

### Post by Hippytaff on 2010-12-09
Nice - as soon as I get chance (and work it out fgrab?) I'll show you mine, not quite as good as yours (though the choice of font isn't for me) but it will be nice to show someone who appreciates this stuff and isn't baffled and confused by both my enthusiasm for it and it it's self (I'm obviously referring to my wife here who greets my geeky sohwings off with a blank vacant expression and askes if I've taken the bins out yet - which I usually haven't :-) )

---

### Post by TiBaal89 on 2010-12-09
All this fun has pushed me off the deep end... I'm currently playing around with installing Gentoo on an old machine.  Cool learning experience!

---

### Post by Hippytaff on 2010-12-09
> **TiBaal89 said:**
> All this fun has pushed me off the deep end... I'm currently playing around with installing Gentoo on an old machine.  Cool learning experience!

My word, that is the deep end :-)

---

### Post by nothingspecial on 2010-12-09
> **Hippytaff said:**
> Nice - as soon as I get chance (and work it out fgrab?) I'll show you mine,

That`s not my normal setup, I just made it for illustration. Far too busy for me..........

....... meanwhile, back at my usual box

[ATTACH]177938[/ATTACH]

That`s dvtm split vertically, I increase the width of of the right side with Ctrl-G then L.

Right side has byobu with irssi, elinks, alpine and a shell.

Left side is another screen with squeezeslave (music player) top, tty-clock middle and another shell for whatever at the bottom.

And a sensible font :P

---

### Post by nothingspecial on 2010-12-09
> **Hippytaff said:**
> and work it out fgrab?

for fbgrab (if you don`t want fbgrab itself in the shot), switch to another tty then type
```

fbgrab -s 2 blah.png
```

change the 2 for the amount of seconds you want to delay it and blah for what ever you want to call your shot.

Then quickly switch back to the tty you want a shot of before the delay.

---

### Post by Hippytaff on 2010-12-09
Pretty basic, but I like it (Ihave a terminal screen in the bottom middle for doing stuff, so didn't bother with -s 2, but very useful tip) :-)

not bad for a noob :-D

hang on - the attachment isn't here :-s

---

### Post by Hippytaff on 2010-12-09
forgot to name it .png

here it is :-)

---

### Post by 12apennachi on 2010-12-09
Can you just install aptitude and apt-* on any random distro so it is really easy to get software? Or is it exclusive to debian/ubuntu? 'cause that would be pretty sweet.

---

### Post by nothingspecial on 2010-12-09
apt is debian and debian derivative specific.

It is probably possible to install it on something else, this is linux after all.

If you do it, I want instructions :D

---

### Post by nothingspecial on 2010-12-09
Sorry about this but another really useful tip has just occurred to me.

You can monitor a window for activity........

I don`t know how mutt works (I am after all a disciple of Master Kmandla). I use alpine. As you get a new email, it appears in your alpine window.

This is where the monitoring comes in handy. If you set your alpine window to be monitored then you will get a notification every time you get an email. It appears in the bottom right hand corner of your window.

To monitor a "window", while it is focused do Ctrl-A then M (that`s Shift-M). Any new activity in that window will then give you a notification. Usefull if you are using the forums and someone replies to a subscribed post.

Who needs those fancy bubbles that pop up in gnome?:p

You can also monitor a window for inactivity with Ctrl-A then _ 

Useful when you are downloading, compiling etc etc.

---

### Post by Hippytaff on 2010-12-09
just debian based stuff I think, though Fedora (redhat based distros) uses yum like deb uses apt :-)

---

### Post by nothingspecial on 2010-12-09
> **Hippytaff said:**
> forgot to name it .png

here it is :-)

Glad to see you have **[Motho ke motho ka botho]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBQQFjAA&url=http%3A%2F%2Fkmandla.wordpress.com%2F&rct=j&q=kmandla&ei=U0ABTe6QF52ShAfLxfnsBw&usg=AFQjCNEFs44tCJed9KKsyZwnqdnftC8VNw&sig2=FYDYAVEBecBSj1a2mQqNBw&cad=rja")**

at the top of your bookmarks :D

---

### Post by Hippytaff on 2010-12-09
The guru of gurus ;-)

---

### Post by nothingspecial on 2010-12-09
It`s tty-clock that shows we`re just disciples :D

---

### Post by Hippytaff on 2010-12-09
tty-clock rules!

however, even after all my potching framebuffer support still refuses to play nice...I knoe it works because the INX live cd proved it :-s

grrr

---

### Post by nothingspecial on 2010-12-10
> **Hippytaff said:**
> tty-clock rules!

however, even after all my potching framebuffer support still refuses to play nice...I knoe it works because the INX live cd proved it :-s

grrr

What`s the problem with the framebuffer?

Did you add yourself to the video group?

Maybe you should create a udev rule

Try this
```

sudo mkdir /etc/udev/my-rules.d
``````
sudo nano /etc/udev/my-rules.d/framebuffer.rules
```Put this in there

```
KERNEL=="fb0",  OWNER="user", MODE="0640"
```
Change user for hippytaff or whatever your username is.
Reboot.

If that doesn`t work, just remove it.

---

### Post by Hippytaff on 2010-12-10
I haven't tried that yet, installed fbterm, tested with links2 -g and  got these errors. Error1 is when I attempt to start links2 -g without  sudo. Fine. error2 is with sudo, so I guess it needs some configuring by setting the mouse option and using mode switch to select the resolution?

---

### Post by nothingspecial on 2010-12-10
For links2 -g you need to install mouse support

```
sudo apt-get install gpm
```

Then you can copy and paste aswell.

To copy and paste in byobu/screen

Ctrl-A then [

Then use your arrow keys to navigate to the start (or end) of the text you wish to copy.

Press space, again with the arrow keys go to the end (or start) of the text then press space again.

To paste, just Ctrl-A then ] 

Useful if you split byobu between elinks and irssi (which I`m sure I`ve spotted you on <unless there is another Hippytaff>)

---

### Post by Hippytaff on 2010-12-10
> 
unless there is another Hippytaff

there is only one hippytaff ;-)

---

### Post by Hippytaff on 2010-12-10
Before I waste a lot of time and brain pain, am I right in thinking /etc/vga/libvga.config needs configuring before fbterm will work (I'm guessing it's just uncommenting the bits you want)

I know, I'm one of those annoying fairly-noobs :roll:

---

### Post by nothingspecial on 2010-12-10
Shouldn`t do, although if you`ve been messing already............

adding yourself to the video group should do it.

---

### Post by Hippytaff on 2010-12-10
Any ideas on how to resolve this?

---

### Post by nothingspecial on 2010-12-10
Yeah, install gpm

You sure you`ve not been smoking???

<I`ve seen your debian thread> :p

---

### Post by Hippytaff on 2010-12-10
haha...I did install it :-)

and no, I have had a small glass of whiskey though :-) it's Friday :-D

```

hippytaff@hippytaff:~$ get gpm
[sudo] password for hippytaff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gpm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hippytaff@hippytaff:~$ 

```
got an alias so get is sudo apt-get install (you knew that though)

---

### Post by nothingspecial on 2010-12-10
> **Hippytaff said:**
> 
[/code]got an alias so get is sudo apt-get install (you knew that though)

I did, mine's "ins"

I can`t understand why this is not working for you.

I do this all the time

try this

```
links2 -g -driver fb
```

---

### Post by Hippytaff on 2010-12-10
I get
```

cannot open gpm mouse

```

---

### Post by cgroza on 2010-12-10
> **Hippytaff said:**
> forgot to name it .png

here it is :-)

May I have a list with the application you use in the screenshot?

---

### Post by nothingspecial on 2010-12-10
> **Hippytaff said:**
> I get
```

cannot open gpm mouse

```

This is doing my head in.

It works for me, on 64bit server and pc; and 32 bit laptop and netbook.

<thinks>

---

### Post by sisco311 on 2010-12-10
> **Hippytaff said:**
> I get
```

cannot open gpm mouse

```

make sure that gpm is configured properly (/etc/gpm.conf) and is running:
```
sudo /etc/init.d/gpm restart
```

If you want to use directfb instead of fb, you have to change the resolution. You can use the GRUB_GFXPAYLOAD_LINUX variable in /etc/default/grub:
```
...
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=1024x768
...
```

For a list of available resolutions run:
```
sudo hwinfo --framebuffer
```

In case you use directfb, you need read and write permissions for /dev/input/mice to be able to use the mouse.

---

### Post by sisco311 on 2010-12-10
Talking about directfb, is anyone else using Qingy?

[[img]http://ompldr.org/tNmlmYw[/img]](http://ompldr.org/vNmlmYw)

---

### Post by Hippytaff on 2010-12-10
> sudo /etc/init.d/gpm restart
that did it...cheers :-)

---

### Post by tame_lx_tech on 2010-12-13
My wifi doesn't connect if i go straight into tty, i have to log in on gnome then got to tty. Any thoughts?

---

### Post by nothingspecial on 2010-12-13
> **tame_lx_tech said:**
> My wifi doesn't connect if i go straight into tty, i have to log in on gnome then got to tty. Any thoughts?

wicd-curses

---

### Post by tame_lx_tech on 2010-12-14
thanks, i'll try that when i get home

---

### Post by 12apennachi on 2010-12-14
I don't know if anyone cares or not, but as I am sure most of you know, facebook isn't accessable from the command line. I was messing around and tried the mobile version of facebook and it worked. m.facebook.com. So you can go on facebook hippytaff. 
Although I kinda realized I mostly go on and look at pictures, but still, it's there.

---

### Post by Hippytaff on 2010-12-14
> **12apennachi said:**
> I don't know if anyone cares or not, but as I am sure most of you know, facebook isn't accessable from the command line. I was messing around and tried the mobile version of facebook and it worked. m.facebook.com. So you can go on facebook hippytaff. 
Although I kinda realized I mostly go on and look at pictures, but still, it's there.

Good find! just goes to show - perseverance will succeed (usually) ;-)

---

### Post by nothingspecial on 2010-12-14
You can facebook chat with bitlbee.

[http://wiki.bitlbee.org/HowtoFacebook](http://wiki.bitlbee.org/HowtoFacebook)

I don`t do facebook, but I do use it with twitter.

I don`t tweet (think I`ve made 2 tweets in 18 months), but I like to follow.

[http://wiki.bitlbee.org/HowtoTwitter](http://wiki.bitlbee.org/HowtoTwitter)

---

### Post by 12apennachi on 2010-12-14
> **nothingspecial said:**
> You can facebook chat with bitlbee.

[http://wiki.bitlbee.org/HowtoFacebook](http://wiki.bitlbee.org/HowtoFacebook)

I don`t do facebook, but I do use it with twitter.

I don`t tweet (think I`ve made 2 tweets in 18 months), but I like to follow.

[http://wiki.bitlbee.org/HowtoTwitter](http://wiki.bitlbee.org/HowtoTwitter)

Yeah same here. I mostly laugh at stupid kids' comments. Still entertaining.

---

### Post by 12apennachi on 2010-12-19
Another question. This one is about mplayer playing movies fullscreen in color. When I mplayer -zoom -x 1366 -y 768 -fs filename.avi in a terminal I get perfect fullscreen color. When I do it in ttyx, I get a black and white picture with only partial fullscreen. Is this normal, or is this not right?

---

### Post by nothingspecial on 2010-12-20
That works for me in colour.

Do you have the correct resolution?

Type ```
fbset
``` to find out.

Also try manually specifying the video output manually

```
-vo fbdev
```

0r```
 -vo fbdev2
```

---

### Post by tame_lx_tech on 2010-12-21
my framebuffer doesn't show anything. i've tried
```

mplayer ~/ep1.mp4 -vo fbdev

```
the audio will play but no video

---

### Post by nothingspecial on 2010-12-21
It won`t work within other apps such as screen, dvtm, twin etc

---

### Post by Alpha101 on 2010-12-22
Posting from Elinks.
I've dl'd mutt, irssi, cmus, I've gotten a better grasp on CLI, and know a few more commands.
I have not yet had to use GUI for anything but visiting my university website. 
So much faster, so much less crap blinking at my eyes, wanted to thank alot of y'all for the help, and new download ideas.
Hope you all have a wonderful Christmas/Holiday.

---

### Post by tame_lx_tech on 2010-12-23
> **nothingspecial said:**
> It won`t work within other apps such as screen, dvtm, twin etc

i'm just running it on tty1, nothing else running

---

