---
title: "How can Nautilus display modification dates consistently, not relatively?"
date: 2020-12-29
forum: Desktop Environments
---

### Post by Paddy Landau on 2020-12-29
A number of apps display dates and times relatively (like "yesterday") or otherwise inconsistently. That's fine, I guess, for a casual user who only occasionally looks at dates and times, but not for me — I find it confusing and distracting.

Normally, these apps give an option to format dates. For example, the default listing for [FONT=courier new]ls[/FONT] is a bit of a mishmash as follows.
```
$ ls -l
total 0
-rw------- 1 paddy paddy 0 Dec 22 02:34 last-week
-rw------- 1 paddy paddy 0 Feb  3  2019 last-year
-rw------- 1 paddy paddy 0 Mar 12  2020 march
-rw------- 1 paddy paddy 0 Dec 29 10:05 today
-rw------- 1 paddy paddy 0 Dec 28 15:15 yesterday
```
But it's easy to change with an option.
```
$ ls -l --time-style='+%F %T' 
total 0
-rw------- 1 paddy paddy 0 2020-12-22 02:34:16 last-week
-rw------- 1 paddy paddy 0 2019-02-03 18:06:14 last-year
-rw------- 1 paddy paddy 0 2020-03-12 09:16:30 march
-rw------- 1 paddy paddy 0 2020-12-29 10:05:00 today
-rw------- 1 paddy paddy 0 2020-12-28 15:15:00 yesterday
```
Nautilus, however, doesn't seem to have an option to change the format. Here is my display in Nautilus for the same files.
[ATTACH=CONFIG]287647[/ATTACH]
Having mixed formats makes it extremely hard to compare dates.

After some searching, I came across only three solutions.

[LIST=1]
[*]Change the source code and recompile Nautilus. This is out of my depth, and anyway it'll be overwritten when there's an update.
[*]Don't use Nautilus. Use something else. Well, I suppose that's an option, but I don't like this. Not only am I very used to Nautilus (I've used it since I first upgraded to Linux), but also I have a few Nautilus scripts that I'd prefer to keep.
[*]An [outdated solution from Ask Ubuntu]("https://askubuntu.com/a/1018026/2088"). Unfortunately, this doesn't work for me. Given the error messages displayed in the terminal when running Nautilus, I suspect that it's to do with a deprecated command in an old version of Python. As I don't know Python at all (I know Bash and nothing else), this is not something that I can debug.
[/LIST]
Do you know how I can use a fixed-format date? I'd like something easy to read, specifically YYYY-MM-DD HH:MM:SS.

More information:

[LIST]
[*]Ubuntu 20.04
[*]Gnome 3.36.8
[*]Nautilus 3.36.3-stable
[/LIST]
Thank you

---

### Post by dino99 on 2020-12-29
You have a good point to discuss on [https://gitlab.gnome.org/GNOME/nautilus/-/issues](https://gitlab.gnome.org/GNOME/nautilus/-/issues)  :P

Myself have not digged around internal nautilus conf via dconf, sorry.

---

### Post by Paddy Landau on 2020-12-29
I have looked at dconf, but as far as I can tell, there is no such option.

Thank you for the link. I've raised a [ticket for the issue]("https://gitlab.gnome.org/GNOME/nautilus/-/issues/1713").

---

### Post by dino99 on 2020-12-29
Hm, already discussed, and yours marked as dupe of [https://gitlab.gnome.org/GNOME/nautilus/-/issues/949](https://gitlab.gnome.org/GNOME/nautilus/-/issues/949)
but lot of possible workaround too :p

---

### Post by The Cog on 2020-12-29
Can I suggest that you use thunar instead. This is the default file manager for Xubuntu. It looks rather like nautilus but has more display options, such as a compact list, and date format customisation. I use it on Ubuntu and it just makes nautilus look crippled.

---

### Post by Paddy Landau on 2020-12-29
> **dino99 said:**
> Hm, already discussed, and yours marked as dupe of [https://gitlab.gnome.org/GNOME/nautilus/-/issues/949](https://gitlab.gnome.org/GNOME/nautilus/-/issues/949)
but lot of possible workaround too :p
Thanks, I saw that. I've also replied to the rather sceptical person who asked me why I want it.
> **The Cog said:**
> Can I suggest that you use thunar instead. This is the default file manager for Xubuntu. It looks rather like nautilus but has more display options, such as a compact list, and date format customisation. I use it on Ubuntu and it just makes nautilus look crippled.
I'll download it and try it out, thanks. If I like it, I'll have to find out how to use it on my desktop instead of Nautilus.

---

### Post by #&amp;thj^% on 2020-12-29
Paddy, what dose this show?
```
gsettings get org.gtk.Settings.FileChooser date-format
```
The default is "regular", the other option is "with-time".
_Never mind I once again skimmed through your thread_, Thunar would be my suggestion as well...

---

### Post by Paddy Landau on 2020-12-29
> **1fallen said:**
> … Never mind I once again skimmed through your thread
Thanks. Interestingly, now that I use "Modified - Time" as the time column, I cannot change it to something else! I change it in Nautilus's settings, but even if I quit Nautilus and restart it, it still shows "Modified - Time" — even though Nautilus's Settings show otherwise! Quite bizarre.

It's OK, because I want to stick with "Modified - Time", but still.

---

### Post by #&amp;thj^% on 2020-12-29
> **Paddy Landau said:**
> Thanks. Interestingly, now that I use "Modified - Time" as the time column, I cannot change it to something else! I change it in Nautilus's settings, but even if I quit Nautilus and restart it, it still shows "Modified - Time" &#8212; even though Nautilus's Settings show otherwise! Quite bizarre.

It's OK, because I want to stick with "Modified - Time", but still.

well you got me thinking on that
can you revert the change any time with: (I know you were of OK with the present setting, but check to see if this works)

```
dconf write /org/gnome/nautilus/preferences/default-sort-in-reverse-order
```
or:
```
gsettings reset org.gnome.nautilus.preferences default-sort-in-reverse-order
```

or:
```
dconf reset /org/gnome/nautilus/preferences/default-sort-in-reverse-order
```
or:
```
 gsettings set org.gnome.nautilus.preferences default-sort-in-reverse-order true
``` 

Note that it applies to whatever the default sort order is, so for example if you change back to sort-by-name that will be reversed as well - _there doesn't seem to be a way to specify the sort direction individually._

---

### Post by Paddy Landau on 2020-12-30
> **1fallen said:**
> can you revert the change any time with…
Nope. I also tried changing confirm-trash, and that too didn't work. I quit Nautilus each time I made a change ([FONT=courier new]nautilus [/FONT][FONT=courier new]--quit[/FONT]) to force it to reload.

On the other hand, doing it in reverse, i.e. changing the settings from within Nautilus, does change dconf. It seems that Nautilus changes dconf, but doesn't read dconf. Does Nautilus have a "secret" place where it stores settings?

Searching further, I see that [FONT=courier new]~/.config/nautilus[/FONT] contains one file called [FONT=courier new]search-metadata[/FONT], which was changed a few minutes ago when I was testing. Its contents read:
```
[directory]
nautilus-list-view-sort-column=search_relevance
nautilus-list-view-sort-reversed=true
```
It's strange!

---

### Post by #&amp;thj^% on 2020-12-30
> **Paddy Landau said:**
>  I quit Nautilus each time I made a change ([FONT=courier new] [/FONT][FONT=courier new]--quit[/FONT]) to force it to reload.



Paddy you know I mean no dis-respect, when I  last used Gnome 16.04, the more terminal use with nautilus within, the more unstable my system became.(Granted I'm not your typical user as a tester)
My point is that could have mucked things up, there's a lot going on inside with snaps .debs systemd you get my drift here. :) BTW FTR Nautlius is not a part of Gnome.
> **Paddy Landau said:**
> Nope. I also tried changing confirm-trash, and that too didn't work. I quit Nautilus each time I made a change ([FONT=courier new]nautilus [/FONT][FONT=courier new]--quit[/FONT]) to force it to reload.

**_On the other hand, doing it in reverse, i.e. changing the settings from within Nautilus, does change dconf. It seems that Nautilus changes dconf, but doesn't read dconf. Does Nautilus have a "secret" place where it stores settings?_**

Searching further, I see that [FONT=courier new]~/.config/nautilus[/FONT] contains one file called [FONT=courier new]search-metadata[/FONT], which was changed a few minutes ago when I was testing. Its contents read:
```
[directory]
nautilus-list-view-sort-column=search_relevance
nautilus-list-view-sort-reversed=true
```
It's strange!
Interesting, more thought needed on my part....any added sym-links by you?

---

