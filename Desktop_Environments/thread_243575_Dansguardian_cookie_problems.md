---
title: "Dansguardian cookie problems?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by cspaz on 2006-08-25
I followed one of the how-to's for installing Dansguardian/tinyproxy/firehol I found on these fourms and it works beautifully, with one tiny snag: cookies aren't working properly.  For example, when I try to login to Flickr, I get a notification that my browser (Firefox) doesn't have cookies enabled.  I've checked and double-checked and it does have cookies enabled.  Also, some of the phpBB based forums I visit don't retain my login info, even though I check the little box for "Remember Me."  So, has anyone else had this kind of problem with Dansguardian not passing cookies properly?

---

### Post by cspaz on 2006-08-25
*BUMP*

Anyone?

---

### Post by cspaz on 2006-08-26
Huzzah, help!

</sarcasm>

:-s

---

### Post by m_p_m on 2007-01-28
Just found this thread, but there is no answer. I have the same problem and would like to know what to do.

I use dansguardian/tinyproxy and works fine otherwise. Just cookies can't be set on the flickr site.

Has anyone figured this out?

thanks
Marco

---

### Post by tonhou on 2007-01-31
I did think that tinyproxy could be the culprit here. 

If you look at the basic overview info on the tinyproxy page ([http://tinyproxy.sourceforge.net/](http://tinyproxy.sourceforge.net/)) you will see "anonymous mode" mentioned and how this can block cookies.

However this needs to be especially uncommented in the tinyproxy.conf file which it is unlikely to be as by default it is commented out.

--Tony

---

### Post by m_p_m on 2007-01-31
Thanks for your post, Tony!

I think you are right about the problem being with tinyproxy (if I go directly though the proxy port 3128, and bypass dansguardian, the problem exists.

I made the suggested change, but no success. It is strange that I can log into my yahoo fine, but not into flickr, even though to me it seems the same login page.

Can you think of anything else?

Many thanks
Marco

---

### Post by glenn69 on 2007-02-20
I've apparently been experiencing the same problem.  I've tried to login to a Moodle site and have received the "Apparently cookies are not enabled" error also.

Unfortunately, I have not yet discovered a fix.  Will keep you posted.

---

### Post by firewren on 2007-04-09
I didn't find a solution to the Tinyproxy issue but I found that switching to Squid for the proxy was an easy fix to get Dansguardian up and running again.

---

### Post by martinquested on 2007-11-28
It seems to be firehol, which is also set up as part of the dansguardian configuration.  If you ```
sudo nano /etc/firehol/firehol.conf
``` and comment-out the line
```
transparent_squid 8080 "nobody root"
```
(i.e. add a # at the start of the line),
then save it (ctrl-x, y, enter) and then type
```
sudo firehol stop
sudo firehol start
```
you should now be able to log in to flickr.

However, to get dansguardian working properly, you will have to repeat the procedure and this time remove the # again.  So you'll need the "keep me logged into flickr" option set before you do that.

I wonder if there is a better way to fix it than this...

---

### Post by martinquested on 2007-11-28
PS It's taken me ages to work this out, since I don't usually sign out of flickr so I hadn't come across this since, evidently, some part of the dansguardian/tinyproxy/firehol setup was (over) strengthened.  So I'm not impressed, but pleased finally to have fixed it - sort of.

---

### Post by martinquested on 2007-12-06
PPS If you use the tab-completion on sudo nano /etc/firehol/firehol.conf you may not succeed, since the firehol directory may not have eXploring permissions set.  Simply type the command out in full and you'll be fine though.

---

### Post by LRT on 2008-01-02
i'm having the same problem.. are there any real solutions to this???? anyone????

---

### Post by martinquested on 2008-01-03
I haven't found anything better than the disabling of firehol, which unfortunately isn't really ideal, since it bypasses Dansguardian.  I feel sure it means flickr etc is serving bad cookies.

---

### Post by LRT on 2008-01-03
i agree... i emailed flickr support, they were no help at all. the cookies don't seem to play nice with firewalls... others have this same problem in other countries... [http://www.flickr.com/help/forum/en-us/61854/]("http://www.flickr.com/help/forum/en-us/61854/")

---

