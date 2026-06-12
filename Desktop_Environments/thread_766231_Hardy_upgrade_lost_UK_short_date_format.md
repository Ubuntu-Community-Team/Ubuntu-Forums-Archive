---
title: "Hardy upgrade lost UK short date format"
date: 2008-04-25
forum: Desktop Environments
---

### Post by Terrycymru on 2008-04-25
After upgrading to Hardy I have lost the UK short date format DDMMYYYY and now have the US format MMDDYYYY across all applications.

I have checked etc/environment and it shows the correct line:
LANG="en_GB.UTF-8"

How can I get the UK format back?

Later: I've also tried making a change in System>Administration>Language Support which is set by default to English (United States). I can select English (United Kingdom) but it will not save the setting. I don't know if this has any relevance to the date format problem.

---

### Post by Terrycymru on 2008-04-26
Bump.

---

### Post by Terrycymru on 2008-04-27
I have reported problem as bug #222570.

---

### Post by bagvian on 2008-08-28
Hello there,
It seems that I have got the same problem than you after installing a 8.04 from scratch.
Did you manage to find a solution?
Cheers, Bagvian

---

### Post by Terrycymru on 2008-08-28
> **bagvian said:**
> Hello there,
It seems that I have got the same problem than you after installing a 8.04 from scratch.
Did you manage to find a solution?
Cheers, Bagvian

Hi Bagvian, I've had to fix a number of issues relating to locale so I am not sure what fixed what. Try this:

1. Logout
2. On login screen click on Options (on bottom left of screen)
3. Select Language
4. Log back in and hopefully it will be saved

Please post back here if it solves your problem.

---

### Post by seadart on 2008-08-28
I had a similar problem but with an original load of 8.0.4 - This solved it - thanks!

---

### Post by bagvian on 2008-09-01
Hi,
I first re-installed the language-pack-en as well as language-pack-en-base through synaptic.
Nothing changed!
I then tried what was suggested by Terrycymru:
1. Logout
2. On login screen click on Options
3. Select Language (I selected English UK)
4. Log back in
Next, it only asks you whether you want to use this language only for this session. 
I then launched Thunderbird and this time dates were displayed properly!
Thanks everybody,
Bagvian

---

### Post by tkking on 2008-10-27
Same problem here on a fresh install of 8.04. Sorted now thanks to this thread.

---

### Post by Benchrest on 2008-10-31
I am in the US and after installing 8.04 I had the wrong date format on the desktop and all applications. I found I had mistakingly chose English America Canada. I probably selected the wrong location on the map. Anyhow I found going to System/Administration/Language Support it showed I was English Canadian. I changed it to English US and rebooted.

---

