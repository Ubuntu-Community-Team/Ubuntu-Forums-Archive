---
title: "Cinnamon/Nemo bulk renaming (Thunar and white space)"
date: 2018-03-30
forum: Desktop Environments
---

### Post by kazakore on 2018-03-30
I've mainly used XFCE but giving a couple of other DEs a try to see whether I may change once I upgrade to 18.04. The bulk renaming facility of Thunar is something I use quite a lot! Good news is it seems it should be easy to use this aspect of Thunar from Nemo (and possibly other file managers.)

Following this guide I have configured the bulk rename in Nemo to open the Thunar bulk renaming.

[https://community.linuxmint.com/tutorial/view/1935](https://community.linuxmint.com/tutorial/view/1935)

It only works when the path and filename have no white space in them though! This makes it basically useless for me! Is there any way to configure how paths and/or whitespace is passed with the url? From editing the command to only open Thunar I get an error message where it looks like the spaces are being replaced with zeros (0) rather than unicode (%20) or encapsulated in quotation marks (""). Anybody know if something can be done about this?

---

### Post by TheFu on 2018-03-30
Whitespace is the default delimiter for many programs.

I decided long ago, to never let filenames or directory names have funny characters or whitespace in them.  Using the rename tool - it is a perl script - to convert all " " into "_" is pretty easy for all files in a directory. Doing it recursively shouldn't be hard using  find + xargs.

Sorry, I have no idea how to do it with a GUI. 

BTW, do you realize that you can change the file manager to anything you want for any desktop, right?

---

### Post by kazakore on 2018-03-31
> **TheFu said:**
> 
BTW, do you realize that you can change the file manager to anything you want for any desktop, right?

Yeah and if I go with it in the longer term and there's no solution to this that is probably what I'll do (it's actually what I did yesterday at when working with files I'm likely to need to rename) but when demoing a new environment for a few days I want to at least try and use the default application as much as possible, even if I'm in mind I may change them for something more suited or more familiar down the line....

The page I linked in slightly wrong as well, you don't need the %F argument to send the file location references with the command. I guess the programming change would have to come from within Nemo itself, to encapsulate each file uri in quotation marks, which most programmers should know is good practice anyway so also partly wondered if this may already be fixed in a later version....

---

### Post by TheFu on 2018-03-31
I agree with what you are saying.  

Since I do lots of scripting, it is simply my laziness that doesn't bother to deal with odd characters. I assume most other programmers are lazy too.  It isn't that I don't attempt to handle odd characters, but I might not be 100% complete in doing it everywhere.  Plus there are the different character sets which add some complexities when scripting.

Usually, in compiled code (I did C/C++ for 15 yrs), I didn't have to do much to allow odd characters besides have the character support on the platform. Spaces weren't an issue.  nemo is compiled, but if  it is passing parms through a shell, then the file expansion/delimiter could come from the shell IFS setting.

I'd never heard of nemo before.  Seems a reasonably capable file manager - at least it supports sftp:// without anything special added.  Wish it refreshed lists automatically, but I can understand that others might not want that. I'm not a user of GUI file managers.

Nemo did crash on my 16.04 box after refusing to quit.

---

### Post by kazakore on 2018-03-31
When dealing a lot with files from external sources it can be expected that at least whitespace is going to be fairly common, plus as most things handle it fine now and I personally find it more readable I've actually started using whitespace in names myself now, whereas I used to try and avoid it in general like you seem to.

From a day with each I think I prefer MATE over Cinnamon, which has a default file manager called Caja. This seems fairly similar to Nemo but can't seem to get the bulk renaming working on it at all, plus a couple of other minor niggles, make me feel if I do migrate I'll probably stick with Thunar. Unfortunately the Preferred Applications for file manager doesn't appear to be working as it should though....

I also often agree with handling stuff via the terminal but I DJ so a lot of my renaming is after separating audio files from their source folder into specific folders and then renaming by media file tag (id3 for eg.) For this I will always prefer GUI over CLI. I know it is a rather niche user case though!

---

### Post by cruzer001 on 2018-03-31
Pyrenamer has always been my choice.  I don't use it often, but I do not recall any problems with whitespaces or underscores.

Its in the repositories.

---

### Post by kazakore on 2018-03-31
As per the link in my first post:

"It only takes *directories* as parameters, while *nemo* offers him a *list of files* to rename. This means that you have to *redo* the selection within *pyRenamer* in order to rename the files you want."

Rather than teaching myself a new method of working I think I'll try and stick with Thunar even if I migrate DE. There is very little in Nemo/Caja extra that I would use often, except possibly the ability to show contents from more than one folder within a tab by expanding them. Plus it is nice to stay with the default apps if you feel they are suited to your use, but obviously the same is to be said of not shying away from using an alternative if it suits you better :)

Thanks for all your pointers and suggestions though :)

---

