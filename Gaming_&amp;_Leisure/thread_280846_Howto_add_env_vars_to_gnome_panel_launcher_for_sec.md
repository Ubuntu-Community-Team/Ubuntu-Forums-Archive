---
title: "Howto add env vars to gnome panel launcher for secondlife"
date: 2006-10-20
forum: Gaming &amp; Leisure
---

### Post by archis on 2006-10-20
A question about environmental variables in Gnome panel launchers:

The current alpha client of an amazingly overexposed MMOG defaults to the ALSA sound system, causing hangs - or 'freezes' - from the get-go. This can be circumvented by adding environmental variables to the Terminal command line: To start the game, you invoke the startup script like this

```
[FONT="Courier New"][SIZE="2"]LL_BAD_ALSA=x LL_BAD_OSS=x ./startup script for ludicrous MMOG[/SIZE][/FONT]

```

For convenience, I now want to add a Gnome panel launcher to my desktop, but I get an error message (**Failed to execute** <reads back the whole line including the env variable>, **no such file**) when I try to enter the following into the command line field of the new panel launcher .desktop file

```
[FONT="Courier New"][SIZE="2"]LL_BAD_ALSA=x LL_BAD_OSS=x /home/xx/../startup script for ludicrous MMOG[/SIZE][/FONT]
```

What is the correct command line syntax to use for the panel launcher?

More generally, *can* I add env variables to the command line of a panel launcher, or do I need to set them elsewhere?

---

### Post by archis on 2006-10-20
I suppose I could just wrap it into a script and stop worrying about Gnome dektop standards.. :KS

---

