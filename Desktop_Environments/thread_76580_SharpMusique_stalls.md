---
title: "SharpMusique stalls"
date: 2005-10-15
forum: Desktop Environments
---

### Post by steffen on 2005-10-15
I'm trying to use SharpMusique to purchase music from the iTunes store. I successfully registered an account with iTunes using SharpMusique, and I'm able to search and preview the catalogue.

However, when I click on 'Purchase' the application simply crashes without error message.

I have tried running sharpmusique from terminal, and the message I'm left with after it crashes is:
```
/bin/bash: /tmp/98bd98d5-1a5d-4b7a-8edc-737b94d084f4.html: Ikke tilgang

``` ("Ikke tilgang" meaning no access)

I have tried running Sharpmusique both as my own user, and as root. Same error every time.

The .html files created in /tmp have the following permissions:

```
-rw-r--r--  1 steffen steffen 1528 2005-10-15 15:56 58837eb8-69d3-4a31-b265-643be3ed7d36.html
-rw-r--r--  1 root    root    1528 2005-10-15 16:08 98bd98d5-1a5d-4b7a-8edc-737b94d084f4.html

```
when run as root or my own user respectively.

Anyone know why this is, and how I can be able to buy music?

---

### Post by kamaaina on 2005-10-16
Hello Steffen,
Sorry I have nothing to add except that I am having the same problem:

/bin/bash: /tmp/f9885e9b-23f1-4b17-8e8c-df66dfca6198.html: Permission denied

For anyone who knows what this means, here is the content of the html file that it spits out each time I try to make a purchase:

Object reference not set to an instance of an object
in <0x00018> System.Text.RegularExpressions.Regex:Match (System.String input, Int32 startat)
in <0x00062> System.Text.RegularExpressions.Regex:Replace (System.String input, System.Text.RegularExpressions.MatchAppendEvaluator evaluator, Int32 count, Int32 startat)
in <0x0006e> System.Text.RegularExpressions.Regex:Replace (System.String input, System.String replacement, Int32 count, Int32 startat)
in <0x0004c> System.Text.RegularExpressions.Regex:Replace (System.String input, System.String replacement)
in <0x00034> System.Text.RegularExpressions.Regex:Replace (System.String input, System.String pattern, System.String replacement, RegexOptions options)
in <0x00012> System.Text.RegularExpressions.Regex:Replace (System.String input, System.String pattern, System.String replacement)
in <0x004ab> Utility:MarkupSanitize (System.String text)
in <0x00013> PurchaseDialog:set_Title (System.String value)
in <0x00225> SharpMusique:OnPurchase (System.Object o, System.EventArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x00096> GLib.Signal:voidObjectCallback (IntPtr handle, IntPtr gch)
in (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x008f3> SharpMusique:.ctor (System.String[] args)
in <0x0003f> SharpMusique:Main (System.String[] args)
~
~
(END)



I've tried to reinstall the program with no luck.

Any pointers appreciated!

---

### Post by kamaaina on 2005-10-20
Well, hoping that this topic will gain a little more attention, I'm updating it with my latest progress.
Seemingly out of the blue, SharpMusique has started working again, partially.  I can log in and purchase songs.  When I do however it places a file named: 
"-  - .m4a"
in the specified download directory.  (However, SharpMusique does not create a sub directory for an artist as it used to do).  This file can be opened in totem and plays fine.  
Sometimes however, if I subsequently purshase/download another file without renaming the previous file it will overwrite the last song I bought.  
Or (like the last time I just tried) it won't over write the previous song and will instead act like it is downloading a file but a new file is nowhere in the specified download dir.

something similar is mentioned here:
 [http://ubuntuforums.org/showthread.php?t=79231&highlight=sharpmusique](http://ubuntuforums.org/showthread.php?t=79231&highlight=sharpmusique)


Thanks

---

### Post by idn on 2005-10-20
I can download files fine, althoughit doesnt name the file correctly - maybe try pyMusique? Its a python version of the application.

Maybe post your error on DVD Jon's Blog

---

### Post by steffen on 2005-10-21
The error has already been posted by me in his blog, about a week ago. No reply yet though, and it's still in his moderation queue.

I tried pyMusique, but I'm getting python errors when I install it.

I think the filename issue is related to SharpMusique not being able to download the title of the song. At least in my window pane, the "Title" field is empty. I have to start a preview to figure out which song it is...

---

### Post by idn on 2005-10-21
I think DVD Jon is moving to teh US or something, so maybe hes not answering his blog right now, sorry I couldnt be more help.

---

### Post by steffen on 2005-10-23
I know there should be some causality here, but seemingly unprovoked my SharpMusique suddenly started working. I'm getting song titles in my list, and I'm able to purchase music.

The songs don't have any filename when downloaded, but I consider that a minor problem as for now. Maybe that'll start to miraculously work as well in a few weeks time... :???:

---

