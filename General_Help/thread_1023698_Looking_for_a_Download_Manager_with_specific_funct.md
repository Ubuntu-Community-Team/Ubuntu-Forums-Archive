---
title: "Looking for a Download Manager with specific functions"
date: 2008-12-28
forum: General Help
---

### Post by malleeblue on 2008-12-28
I've looked in so many places for a good download manager I'm going crazy.

Also, I've downloaded these managers but none of them have all the things I'm looking for:
[LIST]
[*]D4X (Downloader for X)
[*][gwget]("http://projects.gnome.org/gwget/")
[*]aria and [aria2]("http://aria2.sourceforge.net/") (along with [aria2fe]("http://aria2fe.sourceforge.net/"))
[*][Retriever]("http://www.halogenware.com/software/retriever.html")
[*][WxDownload Fast]("http://dfast.sourceforge.net/")
[/LIST]

So below is a list of what I'm after and I'm hoping that you know of an application that does them all:
[LIST]
[*]The option to download using multiple chunks
[*]To always be open, ready to accept new downloads
[*]When open, it must have the ability to reside on the panel as just an icon instead of a minimized window
[*]The ability to set a master/global download schedule (I need it to do its downloads between 4am and 9am)
[*]The ability to download from a podcast/RSS feed (eg D4X kept giving an error when trying to download an m4v file from a feed)
[/LIST]

And on the wish-list (therefore not essential) would be:
[LIST]
[*]The ability to download torrents
[*]The ability to set different schedules for different times of day
[*]Browser integration ([FlashGot]("https://addons.mozilla.org/en-US/firefox/addon/220") may be the solution here)
[/LIST]

Now, you may be thinking that the above ones I've tried, and others you're probably thinking of, do what I'm asking, but please consider the following:
[LIST]
[*]I've tried running, for example, gwget as a cron job (to open at 4am and to close at 9am) but the problem here is that it's not always open. I do not want to have to open and close it every time I add a download to the list. If I left it open it was performing the downloads.
[*]Some of the above apps would allow me to set the schedule but it was per download, which is a pain when the download schedule will always be the same.
[*]It mustn't be browser dependent (like DownThemAll) as I like to restart my browser without affecting my download manager or having to revisit it to restart downloads.
[*]Preferably not a KDE solution as I'm concerned with loading all the other KDE files just to run this one app.
[/LIST]

In my travels I've visited these links - [http://brainstorm.ubuntu.com/idea/3828/]("http://brainstorm.ubuntu.com/idea/3828/") and [http://brainstorm.ubuntu.com/idea/2243]("http://brainstorm.ubuntu.com/idea/2243") - so I'm aware that what I'm looking for may not be available at the time of writing, but I figured there's no harm in asking.

**_NB:_** May I request that if you're going to suggest a solution that it at least meets my "what I'm after" list above, thank you.

---

### Post by malleeblue on 2008-12-31
Giving it a *bump*, still keen for some suggestions, thanks.

---

### Post by scratman on 2009-01-02
Do you know of anything that can do this in Windows, because Wine may be your saviour on this one.

---

### Post by malleeblue on 2009-01-02
> **scratman said:**
> Do you know of anything that can do this in Windows, because Wine may be your saviour on this one.
scratman, if I find a Windows application that does what I'm after, will I also have things like browser integration or do I lose some of the features because it's running in the wine environ rather than in the Ubuntu environ.

This aside though, it's surprising how difficult it is to find a download manager for Ubuntu with these fairly basic and standard features.

---

### Post by scratman on 2009-01-03
Any of these come close to what you're after?

[http://www.pctipsbox.com/top-10-download-managers-available-in-ubuntu/]("http://www.pctipsbox.com/top-10-download-managers-available-in-ubuntu/")

Failing that, if there is an open source piece of software anywhere on the net what does what you like, you couls compile it yourself, and then post a link to it on here in case anybody else is interested.

---

### Post by malleeblue on 2009-01-10
> **scratman said:**
> Any of these come close to what you're after?

[http://www.pctipsbox.com/top-10-download-managers-available-in-ubuntu/]("http://www.pctipsbox.com/top-10-download-managers-available-in-ubuntu/")


Thanks for the link scratman, I've busy testing them and yep, some of them come very close, but I'm being fussy. Although close is good, I'm really looking for something right on target. Now I hope I didn't misunderstand some of the apps I tested and as a result post the wrong info. If anyone reading this is an expert in one of these, and my results are wrong, I'd be grateful if you'd let us all know. Anyway, here's how they stacked up against the criteria in my original post:

**Wget & Gwget**
[LIST]
[*]No scheduling
[*]Can't be left open to have downloads added to it without actioning downloads in its list
[/LIST]

**Curl**
[LIST]
[*]No scheduling
[*]Command line, therefore adding downloads is not easy enough. I prefer a capture from clipboard, like with d4x and Multiget.
[/LIST]

**Axel**
[LIST]
[*]No scheduling
[/LIST]

**Wxdownloadfast**
[LIST]
[*]Scheduling is weird (see screenshot at [http://dfast.sourceforge.net/screenshots.html](http://dfast.sourceforge.net/screenshots.html)), seems it has to be set daily?
[/LIST]

**Multiget**
[LIST]
[*]No scheduling
[/LIST]

**aria2**
[LIST]
[*]No scheduling
[*]GUIs like aria2fe are helpful, but still no scheduling
[/LIST]

**Downloader for X (d4x)**
[LIST]
[*]If you change the default download folder it doesn't remember the change
[*]The slowest download speed is 100bytes/sec. This is acceptable but having no download action until my off-peak time would be better. If I close the app then I'll get zero download (naturally) but as I regularly add stuff to my download list the perfect app will be able to stay open all the time.
[*]I'm unable to get it to download an m4v file from a podcast. When I add the m4v file to the list d4x immediately flags it as complete but nothing's been downloaded.
[/LIST]

**KDE KGET**
[LIST]
[*]It's KDE, so I've not installed it (see original post re KDE solutions)
[/LIST]

**Desktop Data Manager**
[LIST]
[*]Doesn't work for me in Ubuntu 8.10 (Intrepid Ibex).
[/LIST]

**Jigdo**
[LIST]
[*]No scheduling
[*]Command line, therefore adding downloads is not easy enough. I prefer a capture from clipboard, like with d4x and Multiget.
[/LIST]

**Aria**
[LIST]
[*]No scheduling
[/LIST]


**DownThemAll! (DTA) and FlashGot**
[LIST]
[*]DTA - no scheduling
[*]FlashGot is more of a go-between app, not a downloader in itself
[*]Both are browser dependent
[/LIST]

> **scratman said:**
> Failing that, if there is an open source piece of software anywhere on the net that does what you like, you could compile it yourself, and then post a link to it on here in case anybody else is interested.

I hope I can find something soon. If I do I'll read up on compiling and make it happen. Seems the problem will be finding something totally suitable.

---

### Post by scratman on 2009-01-11
I just installed Kget, it's a 10mb download, so it looks like it doesn't install a full kde layer.  Even if it does, could you not cope with that?  Failing that, can't you compile Kget?  Or install one of the other solutions and then a piece of scheduling software, there's several in the repos?

---

### Post by oldos2er on 2009-01-11
Use cron or anacron for scheduling.

---

### Post by malleeblue on 2009-01-11
> **scratman said:**
> I just installed Kget, it's a 10mb download, so it looks like it doesn't install a full kde layer.  Even if it does, could you not cope with that?

I considered that, for the sake of possibly finding my download heaven, I could cope with it and so, **_44mb later_**, it's installed. Alas though, ver 2.1.3 doesn't do scheduling (I'm surprised you recommended it actually).


> **scratman said:**
> ...install one of the other solutions and then a piece of scheduling software...?

To use other scheduling software, KGet would need to be closed and then opened as part of the scheduling task. As you know, one of my criteria is that the app can "always be open, ready to accept new downloads". Problem with KGet is the same as with Wget & Gwget - the app can't be left open to have downloads added to it without actioning downloads in its list (unless I manually pause them and that's a hassle, not to mention that they'd need to be manually restarted, and I'm not up at 4am ...... usually).

> **oldos2er said:**
> Use cron or anacron for scheduling.

I've tried cron jobs (see original post) but as mentioned just above to scratman, I need the app to be open so that I can add downloads to it during the day, and not have it start those downloads until 4am the next morning.
[CENTER]---------------------------------------------------------[/CENTER]
So folks, any other suggestions, I'm all ears and keen to try anything?

---

### Post by scratman on 2009-01-12
I'll be honest, I didn't really test the software fully, so I apologise, I didn't realise that there is no scheduler.  However, you could have it load on startup, and then set a scheduler to do the following steps;-

03:59

---

### Post by malleeblue on 2009-02-13
As yet I still have no solution to my needs. If I ever find one I'll post the details here. Until you see that post, feel free to continue to offer solutions for the sake of everyone who reads this thread. Thanks.

---

### Post by izak on 2009-03-23
What a depressing thread :-|. I am migrating my office PC to ubuntu, and would like to find replacement software for flashGet that allows easy scheduling of downloads late at night when nobody needs the bandwidth.

---

### Post by malleeblue on 2009-03-23
> **izak said:**
> What a depressing thread ...
... that allows easy scheduling of downloads late at night when nobody needs the bandwidth.

It's a bit frustrating but don't be depressed. Life goes on.

I thought I should check with you just in case it's not clear. There are applications which allow for scheduling of downloads, like Downloader for X (d4x) or Wxdownloadfast (see [post number 6]("http://ubuntuforums.org/showpost.php?p=6525530&postcount=6") of this thread for the breakdowns) but I'm not happy with them because of things like having to set download schedules per download, or needing to use cron to schedule the opening and closing of the app at the right times.

If these resemble your issues then I guess you'll just have to "watch this space". Hopefully I'll be able to post a solution one day.

Also, I know you wrote "*that allows easy scheduling*", but if you don't mind a bit of a hassle then maybe Downloader for X (d4x) or Wxdownloadfast might work for you.

Hope that helps.

---

### Post by romuald_geo on 2009-03-29
Check out Multiget [http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

---

### Post by malleeblue on 2009-03-30
> **romuald_geo said:**
> Check out Multiget [http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

As I mentioned in the 6th post of this thread, it doesn't do scheduling.

If I missed that feature or if it now has scheduling then I'd be very grateful if you'd post the instructions (or a link to them).

Please remember though, I'm looking for scheduling in line with what I described in the 1st post in this thread.

Thanks to anyone who can help :)

---

### Post by romuald_geo on 2009-04-03
Sorry it actually doesn't allow scheduling.I just hadn't test it myself before replying

---

### Post by malleeblue on 2010-08-06
It's just over 18 months since the original post and I've still not found a solution so I thought I'd give it another little *bump*. If you have any suggestions (please read the first post before suggesting) then I'd love to hear from you. Thanks fellow Ubunters.

---

### Post by malleeblue on 2012-09-09
Wow, I can't believe it's been nearly 4 years since I originally started this thread. I also can't believe that there's still no solution.

I often read posts where people complain that Ubuntu lacks this and that but Windows has had it for years. I also read, usually in the same threads, that such whingers should shut their pie-holes and enjoy the benefits of a volunteer army who try their best. I won't, therefore, add to the big whinge, but I do wonder why someone hasn't grabbed all the best features of a download manager and put them into one. Such an app would kick-butt and dominate the download manager world. It's not like someone has to invent the features, they just have to bring them together into one app.

Just thinking aloud, is all. Try not to crucify me 'free' thinking.

---

### Post by sienile on 2012-09-09
Have you tried [Retriever]("http://www.halogenware.com/software/retriever.html")?

Well, I looked back and yes you have... The only thing that it's missing from your list is the "run as an icon". Running it through AllTray can solve that.

---

### Post by wildmanne39 on 2012-09-09
Old thread closed.

---

