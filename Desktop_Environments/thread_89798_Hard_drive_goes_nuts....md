---
title: "Hard drive goes nuts..."
date: 2005-11-13
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-11-13
This is a problem that I continuously have in Hoary. What happens is that 5-10 minutes after I boot my computer, the hard drive starts clicking away as if it were doing some very intensive work (reading/writing some very large files.) However, I'm doing nothing of the sort. Sometimes I don't have any user apps running in front of me and it goes nuts. This keeps up for about 5 minutes before the OS cuts it out and I can run my apps without problems (sometimes when I listen to my music, Rythmbox skips the songs.) Anyone had this problem before? Any possible solutions?

---

### Post by foolsh on 2005-11-13
sounds like the system is swaping memory how much RAM do you have?

---

### Post by codejunkie on 2005-11-13
[quote=YourSurrogateGod]This is a problem that I continuously have in Hoary. What happens is that 5-10 minutes after I boot my computer, the hard drive starts clicking away as if it were doing some very intensive work (reading/writing some very large files.) However, I'm doing nothing of the sort. Sometimes I don't have any user apps running in front of me and it goes nuts. This keeps up for about 5 minutes before the OS cuts it out and I can run my apps without problems (sometimes when I listen to my music, Rythmbox skips the songs.) Anyone had this problem before? Any possible solutions?[/quote] when it does that check in top and see if updatedb is running. that might be the cause of it because updatedb is indexing the whole harddrive.

---

### Post by kelsey23 on 2005-11-13
How much ram do you have? I would say anything under 256MB is not enough to run Gnome very well.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=foolsh]sounds like the system is swaping memory how much RAM do you have?[/QUOTE]
512 MB. It happens only once when I run in Ubuntu and that's during start-up. All of the other times it behaves well.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=codejunkie]when it does that check in top and see if updatedb is running. that might be the cause of it because updatedb is indexing the whole harddrive.[/QUOTE]
The thing is, I remember a few months back when this was a non-issue, but it popped up all of a sudden. If it was something that I did, then I don't remember...

---

### Post by codejunkie on 2005-11-13
[quote=YourSurrogateGod]The thing is, I remember a few months back when this was a non-issue, but it popped up all of a sudden. If it was something that I did, then I don't remember...[/quote]what makes me think it's updatedb is it runs at startup, it's has to do with two script's in /etc/cron.daily find.notslocate & slocate it indexes the whole harddrive for the file search utilitys to work. usualy you won't notice it running at all on a clean install but after a while when your drive gets cluttered with more and more data, i've noticed it can take longer to run and slow the system like your describing until it's finished indexing the drives.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=codejunkie]what makes me think it's updatedb is it runs at startup, it's has to do with two script's in /etc/cron.daily find.notslocate & slocate it indexes the whole harddrive for the file search utilitys to work. usualy you won't notice it running at all on a clean install but after a while when your drive gets cluttered with more and more data, i've noticed it can take longer to run and slow the system like your describing until it's finished indexing the drives.[/QUOTE]
Ahh... I see. I'm sure I can get rid of some unnecessary files.

---

### Post by codejunkie on 2005-11-13
[quote=YourSurrogateGod]Ahh... I see. I'm sure I can get rid of some unnecessary files.[/quote]you don't have to remove any files if you wan't to keep them, you can just move find.notslocate & slocate from /etc/cron.daily to /etc/cron.weekly and it will only happen once a week but if you move,remove,add a bunch of files and use Places/search for files or locate functions you'll need to run sudo updatedb before it will recognize the changes.

---

### Post by YourSurrogateGod on 2005-11-20
[QUOTE=codejunkie]you don't have to remove any files if you wan't to keep them, you can just move find.notslocate & slocate from /etc/cron.daily to /etc/cron.weekly and it will only happen once a week but if you move,remove,add a bunch of files and use Places/search for files or locate functions you'll need to run sudo updatedb before it will recognize the changes.[/QUOTE]
I've done what you said, hopefully it'll work.

---

