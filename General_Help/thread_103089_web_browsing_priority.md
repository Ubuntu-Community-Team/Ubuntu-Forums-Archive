---
title: "web browsing priority"
date: 2005-12-13
forum: General Help
---

### Post by hdagelic on 2005-12-13
Just one thing that is bugging me alot on any Linux distribution. Web browsing priority is terrible. If I download any file it sucks out almost all of the bandwidth so that the browser (firefox) doesn't get enough. 

When I used the modem I used to wait for a minute or two for a simple web page to load and now with dsl it's better of course but also slow... Under Windows this is solved allright.

So if any of the Ubuntu developers reads this please try to fix that... And tell me if you know that something can be done... 

:p

---

### Post by bb002 on 2005-12-13
I've witnessed this problem with dsl users. Whether they use windows or not. I don't know what it is about dsl but I didn't have it with dial-up(like i could tell anyways) nor do i have it now with my 1Mbit cable vonnection. My only suggestion is to use a download manager and limit its download speed. there is "d4x" in the ubuntu repositories.

---

### Post by hdagelic on 2005-12-13
It's not that I fell in love with Windows, but It's true what I'm telling you. I had a 56K modem and when I was downloading packages or downloading with Firefox page loading was always terribly slow at least 5 times slower then in Windows under same conditions.

For example a week ago I was downloading some packages and the page:

     [http://www.ffdi.hr/squirrelmail]("http://www.ffdi.hr/squirrelmail")

took about a minute to load and when i logged in to view my mail i have to give up after 3 minutes... What should I say: :???:  Is it the kernel's socket priority, maybe I should renice firefox... I don't know.

---

### Post by mlambie on 2006-03-27
When accessing squirrelmail, it may have been slow if your IMAP server uses mbox instead of Maildir as the mail store. We just recently upgraded our mail server and now use Courier, which uses Maildir, and our clients are noticing a severe increase in speed when using squirrelmail.

---

### Post by aysiu on 2006-03-27
[QUOTE=hdagelic]Just one thing that is bugging me alot on any Linux distribution. Web browsing priority is terrible. If I download any file it sucks out almost all of the bandwidth so that the browser (firefox) doesn't get enough.[/quote] Can we change this to say...? > Just one thing that is bugging me alot on any Linux distribution *on my computer*. I've had no such problems, and I don't think most users here have, either.

> 
So if any of the Ubuntu developers reads this please try to fix that... And tell me if you know that something can be done...  Ubuntu developers do not scour the forums looking for bugs. If you believe it's something the developers can fix, [file a bug report](https://launchpad.net/malone) and be as specific as you can about what hardware you're using.

---

