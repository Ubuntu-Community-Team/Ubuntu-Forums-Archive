---
title: "A couple of handy tips for viewing manual pages"
date: 2006-03-03
forum: Desktop Environments
---

### Post by dpm on 2006-03-03
My original intention was to make a recopilation of those often overlooked little things that make linux just pleasant to work with. Well, I haven't quite managed yet, but I've just found a few which I thought I would share. 

** Note:** you will need to have the groff package installed for tips 1 and 4. Typing ```
 sudo apt-get install groff
```at the terminal should do the trick. Otherwise, you can always use synaptic to install groff.

** 1. Try viewing man pages with a browser instead of with the terminal:**

```
man -Hfirefox ls
```You can also use the $BROWSER environment variable, set it to firefox, epiphany or whichever browser you like and then you can just type e.g. '*man -H ls*'. Have a look at the *man* manual for more detailed information (i.e. type '*man man*').

** 2. Yelp, GNOME's help browser, can also double up as info and man pages viewer.** 

Try the following:

```
(ALT+F2) info:coreutils
``````
(ALT+F2) man:ls
```**Note 1:** yelp can only be used as a viewer with the *info:* command if the given info page exists. Usually at the terminal, if there is no info page available for a command, the info viewer defaults to displaying its man page (if available). This is not the case with yelp: if there is no info page for a command being invoked as *info:command*, yelp will not load the man page but rather display an error message. That's why info:ls does not work: the ls command has only a man page and not an info page.

**Note 2:** *yelp* 2.12.1, the version included with Breezy, does not create clickable hyperlinks for info page sections, although the sections can be equally accessed on the left hand side pane. *Yelp* 2.14.1, shipped with Dapper, does create them -which is quite nice.

[B] 3. You can search for a string pattern within a man page by entering a / (forward slash) character and then typing the string.

[/B]You can then press 'n' to jump to the next occurrence of the pattern or 'N' to jump to the previous one. The pattern is a regular expression. Typing '/' and then the pattern searches forward, typing '?' instead searches backwards.

For more info about navigating within a man page, see the documentation for *less*, which is the pager that the man viewer uses for displaying its output. 

```
man less
``` should give you more detailed information.

**4. Converting man pages to postscript for offline viewing with evince:**

Syntax:
* man -t manpage-to-convert > manpage-converted.ps*

Example (converting the sed manpage to postscript):

```
man -t sed > sed.ps
evince sed.ps
```Please feel free to add more things to the list (of course not limited to man or info tips).

Cheers.

---

### Post by timetunnel on 2006-03-03
> (ALT+F2) info:ls
Doesn't work on my Breezy installation. Error message says "Uniform-Ressource-Identifier (URI-Address) is invalid or points to a non-existing file". "info ls" in a terminal works as usual.

On the other hand,
```
(ALT+F2) info:coreutils
```
works.

---

### Post by brentoboy on 2006-04-16
I really wish I could open firefox, and type in the location...

man://ls

and have it do what I expect.
I cant get the 
man -Hfirefox ls
command to work. (i'm in dapper fight 6)
and I cant get the info:ls thing to work either, but

[alt+F2] man:ls
opens exactly what I wish firefox would have opened, so that isnt so bad.

thanks for a useful post!

---

### Post by dpm on 2006-05-01
[quote=timetunnel]Doesn't work on my Breezy installation. Error message says "Uniform-Ressource-Identifier (URI-Address) is invalid or points to a non-existing file". "info ls" in a terminal works as usual.

On the other hand,
```
(ALT+F2) info:coreutils
``` works.[/quote]

It seems that yelp fails to default to the man pages in case the given command hasn't got an info page, as this is the case with the ls command.

I added a note to my original post describing this behaviour:

> Note: yelp can only be used as a viewer for true info pages with the info: command. Usually on the terminal, if there is no info page available for a command, the info viewer defaults to displaying its man page (if available). This is not the case with yelp: if there is no info page for a command being invoked as info:command, yelp will not load the man page but rather display an error message. That's why info:ls does not work: the ls command has only a man page and not an info page.

---

### Post by art on 2006-05-01
[QUOTE=desp]
Please feel free to add more things to the list (of course not limited to man or info tips).
Cheers.[/QUOTE]
I would just add that when searching for a string in the man pages in the terminal with a backslash, to jump to the next occurence of the string hit the 'n' key.

---

### Post by dpm on 2006-05-01
art,

many thanks for the tip, I've just updated the (mini) guide to include that and a couple of things more.

Cheers

---

### Post by dpm on 2006-05-01
[quote=brentoboy]
I cant get the 
man -Hfirefox ls
command to work.[/quote]Sorry, I didn't notice that you probably needed the *groff* package for that. I've updated my original post to mention that.

I guess a ```
sudo apt-get install groff
``` should solve your problem..

[quote=brentoboy]
and I cant get the info:ls thing to work either[/quote] 
That's because the *ls* utility hasn't got an info page. *Yelp* can't find the info page and exits with an error. On the other hand, when you type 'info ls' at the terminal, it doesn't find the info page, either, but it looks for a man page and if it finds it, it displays it. You can see that when doing 'info ls' an at the top of the screen "*File: *manpages**" is shown. That tells you that the info viewer is showing you the man page because it couldn't find a proper info page.

I've also updated the post in order to mention that.

Thanks to all for the feedback.

---

