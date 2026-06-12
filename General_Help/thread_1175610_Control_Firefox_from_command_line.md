---
title: "Control Firefox from command line"
date: 2009-06-01
forum: General Help
---

### Post by mofrikaantje on 2009-06-01
Hi all,

Is is possible to control Firefox - to a certain extent - through the command line? With Rhythmbox for example, the command *rhythmbox-client --next* plays the next song. Are there similar controls for Firefox: closing tabs, previous page, next page, ...? I already know about opening pages (*firefox pageurl*) but I'd like more...

Thanks in advance.


PS: I'm asking this as I'm using Perlbox-voice to voice-control my computer. It works like a charm :guitar:

---

### Post by upbeat.linux on 2009-06-01
I'll have to test it out.

You probably already know about the basic command line options:

[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

I'm guessing you could setup key bindings in FF and then access those from the command line.....

I also wonder if you can control ubiquity from the command line.  Seems like something javascript should be able to do...

Hmmm, interesting thread to watch..

---

### Post by t0p on 2009-06-01
There doesn't seem to be a man page for firefox.  Dunno why - seems like a terrible oversight.  You can get some help thusly:

```
t0p@ubunty:~$ firefox --help
Usage: /usr/lib/firefox-3.0.10/firefox [ options ... ] [URL]
       where options include:

X11 options
	--display=DISPLAY		X display to use
	--sync		Make X calls synchronous
	--no-xshm		Don't use X shared memory extension
	--xim-preedit=STYLE
	--xim-status=STYLE
	--g-fatal-warnings		Make all warnings fatal

Mozilla options
	-height <value>		Set height of startup window to <value>.
	-h or -help		Print this message.
	-width <value>		Set width of startup window to <value>.
	-v or -version		Print Firefox version.
	-P <profile>		Start with <profile>.
	-ProfileManager		Start with ProfileManager.
	-no-remote		Open new instance, not a new window in running instance.
	-UILocale <locale>		Start with <locale> resources as UI Locale.
	-safe-mode		Disables extensions and themes for this session.
  -jsconsole           Open the Error console.

```

but that doesn't seem sufficient for such a large, capable app.  You should ask the devs.  Tell them to pull their finger out!

---

### Post by mofrikaantje on 2009-06-01
Thanks for the other options, didn't find those already - but they aren't quite useful or "complex", as you guys already pointed out. I searched around a bit more and found out there are [a bit more commands available]("https://developer.mozilla.org/en/Command_Line_Options"), I've listed the useful ones:

```
-url URL
-new-tab URL
-new-window URL
-search term

```

Funny enough, "Other options need to be documented", including GTK and X11 options.
Especially the last command is useful, if I succeed in letting the program recognize my voice input and putting it into a search query. There are also a few options available for Thunderbird, but I use the online version of GMail so that's not an option.
About the Javascript bit: [this page]("http://www-archive.mozilla.org/quality/browser/front-end/testcases/cmd-line/") says they're not going to test that through the command line.
I found [this list of XUL commands]("https://developer.mozilla.org/en/XUL/List_of_commands"), which seems useful within the XUL environment, but not outside it - I am searching for commands to directly control Firefox, not some ugly way around. :)
t0p, I followed your advice and posted a question on their support forum ([read it here]("http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=359977&forumId=1")).

Could someone else enlighten us? :popcorn:

Btw: if someone knows where to find command line commands to control Gnome windows, feel free to share ;)

---

### Post by mofrikaantje on 2009-06-02
Just got an answer from the support forums on Firefox, apparently the [commands]("https://developer.mozilla.org/en/Command_Line_Options") quoted above are as much as there is to it. Nothing more available - without add-ons, that is. I've looked around but don't seem to find anything suitable, does anyone else might have some ideas?

---

### Post by danohuiginn on 2011-05-06
The mozrepl add-on will get you much of the way here
[https://github.com/bard/mozrepl/wiki](https://github.com/bard/mozrepl/wiki)

It sets up a telnet interface, from which you can control almost everything in firefox.

---

