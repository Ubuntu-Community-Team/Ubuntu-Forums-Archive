---
title: "Going GUI-less"
date: 2008-10-19
forum: Desktop Environments
---

### Post by BetaMaster on 2008-10-19
Hey,
For whatever reason, I'm interested in going GUI-less, and purely CLI. For the most part, I've got my apps figured out (cplay, elinks, finch, emacs, and screen to use it all) but I had a few questions.

One: How would I manage copying and pasting on the CLI? Is it at all possible? As far as I can tell, the answer is 'no', but I thought I'd ask.

Two: Is it possible to get mplayer to output video to ASCII in the CLI? Using the -vo aa or -vo caca flags don't really work when you're entirely GUI-less, I imagine because mplayer outputs the ASCII video as rendered video.

Three: How would you print in emacs or nano, and can you just 'print screen' to print the current screen's contents?

Four: Is it at all possible to change the display resolution? It's either 640x480 or 800x600, and I'd love it if I could raise the resolution higher. Not a big deal though, and I doubt if it's possible.

Five: This is a more broad question. In general, what are some good CLI programs? Is there a better music player? Anything you'd recommend?

Sorry for all the questions, but I'd love answers to any of them. Thanks!

---

### Post by Dave_Connor on 2008-10-19
To copy and paste in terminal there is ctrl + shift + c to copy and ctrl + shift + v to paste. I think there is gim to have a window manager in cli.

---

### Post by BetaMaster on 2008-10-20
Thanks for the reply, but ctrl+shift+c (and likewise with v) only works after you have selected text, which only seems possible with a cursor. I'm talking about being entirely GUIless, running in TTY1 or something.

---

### Post by bionnaki on 2008-10-20
I use moc for music - it's great.
[http://polishlinux.org/apps/cli/moc-console-audio-player-for-linux/](http://polishlinux.org/apps/cli/moc-console-audio-player-for-linux/)



other cli apps I use:

calc - calculator
rtorrent - the best torrent client ever
mktorrent - for making torrents
htop - system monitor
irssi - irc
finch - instant messenger 

also look into the various email clients and rss readers.

---

### Post by p_quarles on 2008-10-20
Individual applications have cut-and-paste features, but as far as I know there is no shell that has that functionality by itself. 

For printing, there is the 'lp' command, which can certainly send text files (i.e., anything that Emacs can read) to a correctly configured printer.

---

### Post by Sorivenul on 2008-10-20
There were plans for a new CLI distribution going on at the CafeLinux forums [here]("http://cafelinux.org/forum/index.php/topic,1504.0.html").  Some CLI applications are discussed/listed.  

[This site]("http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/GNU-Linux-Tools-Summary.html") has a nice introduction, IMO.

What are you planning to do on this machine, other than learn?  There are lots of possibilities, and we can guide you, but specific information about what you want to gain will help.

EDIT:
Forgot a few more helpful links.
[http://www.cli-apps.org/]("http://www.cli-apps.org/")
[Essential Command Line Apps for Common Tasks]("http://www.hackosis.com/2007/12/29/linux-essential-command-line-apps-for-common-tasks/")

And don't forget SourceForge and LaunchPad.  Plenty to be found to use.

---

### Post by BetaMaster on 2008-10-20
Thanks for all the responses!
@bionacca Thanks, I hadn't heard of moc, I had heard of mp321, but was unable to find it. I'll definitely give moc a try, it looks a lot like cplay, only with more media functionality (you have to cycle between playlist and file browse mode in cplay, for one). I knew about finch, rtorrent, and irssi (and use them) but not the others!

@p_quarles Thanks, I didn't know about lp, so that'll help me.

@Sorivenul *Thanks* for all these links, this'll give me a lot of reading material! As for what do I plan on doing on this machine? Admittedly, not a lot. General use: internet, pidgin(/finch), text editing, maybe some games (the only ones I really know of, though, are nethack and doomRL). There will be exceptions when I use the computer to do something else, of course, but in general, that will be it. Nothing too major. As for what I would like to gain..I'm already comfortable using the command line for basic tasks, but I'd like to get more adept at using it to do more than just navigate, compile, etc.

Sorry if I'm not being specific enough, but I'm trying :)

---

### Post by Sorivenul on 2008-10-20
> **BetaMaster said:**
> As for what I would like to gain..I'm already comfortable using the command line for basic tasks, but I'd like to get more adept at using it to do more than just navigate, compile, etc.
Don't worry, you're giving enough specifics.  :)  It's good to know there are more people out there who want to learn.  I didn't really include my personal suggestions before, but will now, knowing a bit more about what you want.

For word processing (not just text editing) I suggest [WordGrinder]("http://sourceforge.net/projects/wordgrinder/"); it's available on SourceForge and does what it's designed to do.

I have to second moc. finch is a good IM client and you've already mentioned it, and I can't live without irssi.  I personally use links2 for my non-GUI web-browsing and one of the two major editors (vim/emacs) for my editing.  If you don't already know one or both of these, after some time with your CLI system, get to learn one of them at least.  Oh, and if you need more to your file management than the system utilities, mc is my personal favorite for file management, though others opinions may vary.  

Again, good luck to you.

---

### Post by derouge on 2008-10-20
I don't think I saw it mentioned here but if you aren't familiar with GNU's screen application ... get familiar. ;) It will probably be the most useful tool if you decide to go GUI-less.  It's pretty darn useful even if you use a GUI!

You might wanna check out the GPM ([http://freshmeat.net/projects/gpm/](http://freshmeat.net/projects/gpm/)) project for some info on mouse (and I believe copy+paste, though I've never actually used it) support in the console.  Sort of a neat project.

---

### Post by BetaMaster on 2008-10-22
@Sorivenul WordGrinder seems interesting, I'll definitely check it out! I haven't tried links2 before though, only links. Is there much improvement? I've used mc too, and really like it. As for vim or emacs..I have some experience (vim is installed with minix on my old '96 Toshiba Satellite) but I haven't worked with it enough to remember all the key combos, so I find it difficult to use. That being said, knowing how powerful emacs is, I'd probably just as soon skip vim and learn that.

@derouge So GPM adds mouse support to the console? Interesting. Also, I am very familiar with screen ;) It's incredibly useful.

---

