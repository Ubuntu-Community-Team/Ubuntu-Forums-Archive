---
title: "Rar File Help! Urgent!"
date: 2009-05-05
forum: General Help
---

### Post by HiddenDev on 2009-05-05
Well I Need Some Information Please. I Am Currently Downloading A Huge File Its Divided Into 2 Parts 

file.part1.rar and file.part2.rar 

Now Normally If I Was Running Windows I Would Just Run WinRar And It Would Automatically Combine The 2 Files Back How They Are Supposed To Be. But Since Im Running Ubuntu Now I Have No Clue If This Is Going To Work.

Any Help? :smile:

Greatly Appreciated,
Devin

If You All Could Help Me Find The Answer If You Do Not Know It It Would Be Lovely. I Am In Need Of This Urgently.

---

### Post by zero777zero on 2009-05-05
i had this issue last week.

you should check out this thread: [http://ubuntuforums.org/showthread.php?t=1141933](http://ubuntuforums.org/showthread.php?t=1141933)

another option is just to download the official 7z program
[http://www.7-zip.org/](http://www.7-zip.org/)
if you cant get the linux version to work, you can use the windows version through wine

---

### Post by bryncoles on 2009-05-05
I do this all the time. just unzip the files as normal through your right click menu and it will automagically work as expected.

---

### Post by HiddenDev on 2009-05-05
Will This Combine The Parts? And Thanks For Your Reply Ive Been Posting This For 4 Days And 0 Replys.

---

### Post by Grenage on 2009-05-05
I don't believe rar support is native (unless something has changed), but you can easily add it using the package manager by searching for "unrar".  Yes, it will combine the two parts, that's the more common way rar is used.

Alternatively, you can of course use apt-get from the CLI

---

### Post by HiddenDev on 2009-05-05
> **bryncoles said:**
> I do this all the time. just unzip the files as normal through your right click menu and it will automagically work as expected.

Using WinRar or 7-Zip?

---

### Post by cdwillis on 2009-05-05
Right click one of the files and extract it. That's it. You shouldn't need to install anything else as far as I know.

---

### Post by Grenage on 2009-05-05
I don't believe the free version supports segregated archive files, only the non-free version.  The non-free version is available via apt-get or the package manager under the name "unrar".

---

### Post by HiddenDev on 2009-05-05
Alright Ill Find unrar and Install it?

---

### Post by slakkie on 2009-05-05
rar e <first rar file> should do the trick via the cli.


Maybe e is x, haven't used rar in a while, ahh, you can use both for extracting. See the manpage.

I have the rar and the unrar package installed, I only use rar, guess that is in the default repositories (8.04.x)

---

### Post by Grenage on 2009-05-05
Bingo.

System/
Administration/
Synaptic Package Manager/

Type unrar into the search box.
Select it from the list.
Click Apply etc.

Then you can right-click and select "extract here" on your file(s).

---

### Post by HiddenDev on 2009-05-05
> **slakkie said:**
> rar e <first rar file> should do the trick via the cli.


Maybe e is x, haven't used rar in a while, ahh, you can use both for extracting. See the manpage.

I have the rar and the unrar package installed, I only use rar, guess that is in the default repositories (8.04.x)

Will This Combine The Files?


Im So New At This But Grenage Do I Get The Un-free Version and if so do i have to buy it?

---

### Post by Grenage on 2009-05-05
When I say unfree, I'm talking about freedom, not beer :)  The source code isn't open, you don't have to pay any money.

The free version may do what you need.   Double-checking the descriptions says that it's only some ver3 files it can't handle.  If you want to keep it really simple, install the non-free.

---

### Post by HiddenDev on 2009-05-05
> **Grenage said:**
> When I say unfree, I'm talking about freedom, not beer :)  The source code isn't open, you don't have to pay any money.


Ok So unrar Will Combine Both The file1.part1.rar and file1.part2.rar together?

All i have to do is right click and Select Extract Here?

---

### Post by slakkie on 2009-05-05
> **HiddenDev said:**
> Will This Combine The Files?


Im So New At This But Grenage Do I Get The Un-free Version and if so do i have to buy it?

This will unpack all the rar files, just like winrar does, so yes, it will combine files if needed.

---

### Post by HiddenDev on 2009-05-05
Alright Thanks Alot This Has Really Helped Me Even Know I Look Like A 2 Year Old With All The Questions. But Now I Need To Get My D Drive Working. Other Thread Away!

---

### Post by psablo on 2009-05-06
I appreciate the thread.

I too thought "free" meant beer, not code.

so what is the point of unrar-free, it seems to do nothing?

---

### Post by Grenage on 2009-05-06
I believe (from the description) that it can cope with most rar files, but not those created by version 3 or above.

---

