---
title: "Opera 9"
date: 2006-10-05
forum: Desktop Environments
---

### Post by meanmrmustard on 2006-10-05
According to the Ubuntu web site :[http://www.ubuntu.com/news/opera9?highlight=%28opera%29](http://www.ubuntu.com/news/opera9?highlight=%28opera%29)

Opera v9 is supposed to be available in the 'add remove programs' menu in Dapper.
I have both unsupported and commercial boxes checked but Opera isn't there.

Is there an Ubuntu package or not?

---

### Post by pay on 2006-10-05
```
sudo nano /etc/apt/sources.list
```and add this line (if it's not there) at the end of the file```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```then update and install```
sudo aptitude update
sudo aptitude install opera
```

---

### Post by jd65pl on 2006-10-05
There is a package available. I can find it in my add/remove screen. I think you may need to enable the multiverse repository. If you are just learning I think the easiest way to do this is...

Go to *APPLICATIONS > SYSTEM > ADMIN > SOFTWARE PROPERTIES*

Find the choice which says  Ubuntu 6.06 LTS (Binary) then click on the edit button on the right.
Check the option for multiverse in the popup window then click OK until back to the desktop and re-run add/remove

---

### Post by motang on 2006-10-05
> **meanmrmustard said:**
> According to the Ubuntu web site :[http://www.ubuntu.com/news/opera9?highlight=%28opera%29](http://www.ubuntu.com/news/opera9?highlight=%28opera%29)

Opera v9 is supposed to be available in the 'add remove programs' menu in Dapper.
I have both unsupported and commercial boxes checked but Opera isn't there.

Is there an Ubuntu package or not?

Hello well if you are having that much trouble here is a [link]("http://linux.softpedia.com/progDownload/Opera-Download-271.html") so that you can download the .deb file and double click on it.  If you are running ubuntu 6.06 you can just double click on the .deb file and installer will take care of the rest.

Hope this helps you out dude!

---

### Post by meanmrmustard on 2006-11-03
> **jd65pl said:**
> There is a package available. I can find it in my add/remove screen. I think you may need to enable the multiverse repository. If you are just learning I think the easiest way to do this is...

Go to *APPLICATIONS > SYSTEM > ADMIN > SOFTWARE PROPERTIES*

Find the choice which says  Ubuntu 6.06 LTS (Binary) then click on the edit button on the right.
Check the option for multiverse in the popup window then click OK until back to the desktop and re-run add/remove

When I tried this, every time I re-loaded, it gave me a message that the list wasn't up to date and went through the procedure again, and again......

Finally I edited the sources.list by hand adding multiverse to a couple lines (which I had already done, but to the wrong lines)and it finally showed Opera in the add/remove list.

Thanks for everyone's input.

---

