---
title: "Trouble installing Thunderbird 1.5"
date: 2006-01-17
forum: Desktop Environments
---

### Post by Alex99 on 2006-01-17
I already checked the forum, but this seems to be a new one:
I uninstalled Tb 1.0.7 with Synaptic, deleted all the program files by hand as the mozilla manual told me to, downloaded the Tb-1.5.tar.gz (or so), unpacked it, ran the file "thunderbird", and then I got the message (in German - here's a translation -)

```
Thunderbird is currently running, but it doesn't react. In order to open a new window, you need to terminate the running program or restart your computer
```

needless to say, I've tried both steps, but it doesn't make sense.

thanks for your help!
Alex

---

### Post by dabang on 2006-01-17
Did you run "./thunderbird" from the unpacked Thunderbird 1.5 directory or did you run "thunderbird" without "./"? Maybe there's a "thunderbird" file left somewhere in your $Path? Maybe in "/usr/bin"?

---

### Post by Sef on 2006-01-17
Try this from the terminal:

killall thunderbird

(Note: you may have to capitalize the T if thunderbird doesn't work.)

---

### Post by Alex99 on 2006-01-17
running the command "killall" doesn't in fact terminate any processes, no matter if thunderbird is capitalized or not. I don't think there are any thunderbird files left on my system apart from the extracted thunderbird-1.5. folder; the gnome-search-function (places>search) as well as "beagle" don't show me any. However, I'm suspicious of those results since both programs don't tell me about the thunderbird folder that I copied to /opt.
any ideas?

---

### Post by mrmcctt on 2006-01-17
Have you tried the installation isntructions [HERE?]("http://doc.gwos.org/index.php/ThunderbirdNewVersion")

I found the installation instructions for Thunderbird on the mozilla.com site vague to say the least.  Thunderbird seems to be working ok after using the instructions from the link above.

---

### Post by PuNGS on 2006-01-17
I simply got the .tar.gz source and compiled it. It worked perfectly here.

---

### Post by Alex99 on 2006-01-17
Problem solved, thanks for your replies. I finally got the error message in English, googled for it and finally found the solution: my "profiles.ini" directed Tb to a profiles-folder that doesn't exist anymore.

---

