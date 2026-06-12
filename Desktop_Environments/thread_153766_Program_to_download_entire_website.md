---
title: "Program to download entire website"
date: 2006-04-01
forum: Desktop Environments
---

### Post by josh34 on 2006-04-01
Is there a good program for Ubuntu that will download an entire site and has options such as only download pages from that site and only download certain file types?

Thanks,
Josh

---

### Post by Harleen on 2006-04-01
wget can do that. Although it requires some fiddling on the command line.

---

### Post by stoeptegel on 2006-04-01
There's (web)httrack in the repositories, it might do what you want since you can filter it pretty nicely

---

### Post by bakert on 2006-04-02
wget is definitely what you want.  Check out the --reject and -r options.  Plus don't forget --wait and --random-wait and --user-agent else you might upset the website owner!

---

### Post by josh34 on 2006-04-02
I am new to Ubuntu, so could someone explain how to install wget and also how to use some basic functions?

Thanks,
Josh

---

### Post by stoeptegel on 2006-04-02
Yeah sure.
I think wget is default installed on (k)ubuntu, so you can just start reading the manual from a terminal emulator like konsole in KDE or (...what is it called here?...) in GNOME. 

Fire up your terminal emulator and type:
$ man wget [enter]

This should give you much information about an installed program.(arrow to scroll and q to quit)

For this particular purpose i haven't used wget myself, i would have to search in the manual myself to get me the proper command. So i think it's best to wait for someone who has used it for website downloading. (or you wanna try and dive into the man of wget yourself)

---

### Post by josh34 on 2006-04-02
I looked at the manual and it is very confusing. What I basically want to do is download all the pages that are linked on insertdomainhere.com/directory, except for insertdomainhere.com and insertdomainhere.com/anotherdirectory. I would also like to only download pages and files that are only 2 links deep from insertdomainhere.com/directory. I hope you can help.

Thanks,
Josh

Also I would like to tell it to only save .jpg and .jpeg files.

---

### Post by josh34 on 2006-04-04
Anymore ideas?

Thanks,
Josh

---

### Post by stoeptegel on 2006-04-04
I did some testing, but it happens to be more difficult. (i couldn' t get anything of my test website)
You can use $ wget --help to see all the commands though.

---

### Post by phrawzty on 2006-04-04
[QUOTE=josh34]What I basically want to do is download all the pages that are linked on insertdomainhere.com/directory, except for insertdomainhere.com and insertdomainhere.com/anotherdirectory. I would also like to only download pages and files that are only 2 links deep from insertdomainhere.com/directory.

Also I would like to tell it to only save .jpg and .jpeg files.[/QUOTE]

Ah, yes, [FONT="Courier New"]wget[/FONT] can be a difficult beast to master.  What you're looking for is this:

```
# wget -r -l 2 -A jpg,jpeg http://insertdomainhere.com/directory
```

"[FONT="Courier New"]-r[/FONT]" means recursive, so it will follow links automatically
"[FONT="Courier New"]-l 2[/FONT]" restricts the recursiveness to only 2 levels deep
"[FONT="Courier New"]-A jpg,jpeg[/FONT]" tells it to only save .jpg and .jpeg files

---

### Post by josh34 on 2006-04-08
How would I use a proxy with this: # wget -r -l 2 -A jpg,jpeg [http://insertdomainhere.com/directory](http://insertdomainhere.com/directory)

Thanks,
Josh

---

### Post by stoeptegel on 2006-04-08
[QUOTE=josh34]How would I use a proxy with this: # wget -r -l 2 -A jpg,jpeg [http://insertdomainhere.com/directory](http://insertdomainhere.com/directory)

Thanks,
Josh[/QUOTE]

```

wget -U "Mozilla/5.0 (X11; U; Linux i686; nl; rv:1.7.3) Gecko/20040916" -r -l 2 -A jpg,jpeg -nc --limit-rate=20K -w 4 --random-wait   http://insertdomainhere.com/directory http_proxy http://username:passwrd@(ifneeded)yourproxy.com:port -S
```

-nc = for avoiding downloading linked files already downloaded
-w = to wait 4 seconds between retrievals
--random-wait = to make the -w time * 0-2
-U = user-agent
--limit-rate = to mask your download somewhat, 20KB would be nice i think
-S = print server response
http_proxy = does what you asked (note that i don't know wheither wget might automaticly fall back on no proxy or not)

---

### Post by outofnicks on 2006-04-08
Just a quick note for wget in general:
You might want to use the -np option (no parent) to keep wget from ascending to parent directories, where it could download a whole lot more than you desire.

---

### Post by josh34 on 2006-04-23
When I login to a site with Firefox and it makes a cookie, how do I use that cookie when using wget to download a site, so that wget has full access to the site?

Thanks,
Josh

---

### Post by josh34 on 2006-04-25
Again, any idea how to use cookies with wget?

Thanks,
Josh

---

### Post by spade_shark on 2006-04-26
Also try the Burp Suite tools.  I think the spider is what you may want to try.

[http://www.portswigger.net/spider/](http://www.portswigger.net/spider/)

---

### Post by benf101 on 2008-07-05
how about klinkstatus.  It's in the programming folder.

---

