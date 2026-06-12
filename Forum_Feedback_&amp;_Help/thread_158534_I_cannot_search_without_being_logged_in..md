---
title: "I cannot search without being logged in."
date: 2006-04-11
forum: Forum Feedback &amp; Help
---

### Post by steve196 on 2006-04-11
Why is that? You should not be forced, to hand over an email adress, just for searching posts in a forum.

---

### Post by trent dillman on 2006-04-11
You weren't forced. Use Google:

```
search query site:www.ubuntuforums.org
```

---

### Post by aysiu on 2006-04-11
Go to [http://www.google.com](http://www.google.com) and type in ```
site:ubuntuforums.org name of problem
``` It actually is a better search than using the site's search.

---

### Post by steve196 on 2006-04-12
Thank you. 
But I was not actually asking for help. As you see, I am already registered, so this is not my problem. I am asking those, who made the decision, why someone, who decides not to give out his email adress cannot directly search for information here.
The google search is a good thing, but I did not get the idea by myself, even although I know their search syntax. If it is not obvious to me, it is probably not obvious to others.
So, please can one of those, who made that decision explain the reason for it?

---

### Post by K.Mandla on 2006-04-13
I find this change a little disappointing too. I like to jump right in and search for whatever problem I've encountered, right away. But it's another step to have to sign in just to find out why I get vertical lines on Dapper with an I810 integrated graphics card. Can't we have it back the old way? Please? It was much friendlier. :(

---

### Post by ubuntu-geek on 2006-04-13
Guest searching will be turned back on shortly after the alternative search for guest users is completed, to leave it on right now costs to much on the database.

---

### Post by prizrak on 2006-04-13
Is there a possibility of having a refined search that will only search for headlines? Many times I remember the thread name and search for that but it returns everything it finds not just the thread and the thread is rarely on top too.

---

### Post by ubuntu-geek on 2006-04-13
[QUOTE=prizrak]Is there a possibility of having a refined search that will only search for headlines? Many times I remember the thread name and search for that but it returns everything it finds not just the thread and the thread is rarely on top too.[/QUOTE]
Actually yes.. if you goto the advanced search function and under keyword search you will see a drop down that says "search entire post" in that drop down you can select to search titles only.

---

### Post by NeghVar on 2006-04-13
When It comes to the cost to the database. What about shrinking that data base. ALOT of posts are redundant like root/sudo questions and such, all these posts have the same answers and dont need to stay forever.

Just a thought, it would also help new users when they search find useful help on a topic. This way when they search for say 'root password' they don't get 1k + threads, it may seem trivial but I'm talking about the person who has never really used forums or tried another OS than what came preinstalled.

---

### Post by K.Mandla on 2006-04-13
As a side thought, would an alternative search box that redirects through Google be helpful? Rather than telling people to search from the Google page (which is a turnoff), you could simply forward their search term straight to Google with the site:[www.ubuntuforums.org](www.ubuntuforums.org) tacked on at the end. Maybe that's a weird idea. But it might relieve some stress on your database.

---

### Post by aysiu on 2006-04-13
To expand on NeghVar's suggestion, you can make a logged in search come up with everything and a non-logged-in search come up with only the last three months or something...

---

### Post by NeghVar on 2006-04-13
> To expand on NeghVar's suggestion, you can make a logged in search come up with everything and a non-logged-in search come up with only the last three months or something...

Also a plausible sugestion, although I think in the long run removing redundancy would go a long way, I'm not sure how your hosting system works and what not but I bet if you remove a lot of the redundancy and what not it will make this more streamlined.

In the long run assuming we continue to have this problem it could grow to even larger levels than it is now, and it will continue to be a problem until you just start cleaning things out. Although aysiu's suggestion is a good stop gap I don't think it adresses the one year from now when the database continues to grow and such.

---

### Post by aysiu on 2006-04-13
Really, what should be done--and this is one of the things I miss from being a moderator, having the ability to do this--is a whole bunch of redundant threads need to be merged.

What appears to happen a lot is redundant threads get left standing or get closed. Either way, they're another thread out there, another search result.

Next time a KDE v. Gnome thread pops up, it should be merged with the ten other KDE v. Gnome threads out there.

Same for "How do I log in as root?" and "I can't mount my Windows partition."

---

### Post by NeghVar on 2006-04-13
With the newer threads yes, with the older ones, if they offer no new advice on the issue then delete them, merge threads that have different responses/solutions.

---

### Post by aysiu on 2006-04-13
[QUOTE=NeghVar]With the newer threads yes, with the older ones, if they offer no new advice on the issue then delete them, merge threads that have different responses/solutions.[/QUOTE] I don't know about deleting threads.

---

### Post by NeghVar on 2006-04-13
Well if you merge say 10 threads on root/sudo, you get 10 answers that are all the same and the files all take up the same space as before, where as if we remove them altogether it frees up space and gives every1 1 answer.

---

### Post by aysiu on 2006-04-13
[QUOTE=NeghVar]Well if you merge say 10 threads on root/sudo, you get 10 answers that are all the same and the files all take up the same space as before, where as if we remove them altogether it frees up space and gives every1 1 answer.[/QUOTE] Yeah, but then you have to decide which answer is the most worthwhile answer to keep out of the ten answers that are all the same solution.

I don't know too much about databases and bandwidth, but I would imagine most of the cost comes from querying the different threads and then the bandwidth to sort and return the thread results--not in the storage of multiple posts within a thread (unless you click on the thread itself).

Though, I guess the contents of the thread have to be indexed and searched... that's more to index, more to search...

---

### Post by ubuntu-geek on 2006-04-13
Merging won't solve the issue.. In the long term another server will need to be purchased spefically for searching, but in the short term disabling guest searching and using an alternative method (which is being developed) has dropped cpu/db load by 70%..

---

### Post by steve196 on 2006-04-13
Thank you ubuntugeek for the explanation of the issue. 
However I would suggest, that, in addition the login page, a guest clicking on search could get a very short explanation of Googles "site:" syntax.

---

### Post by NeghVar on 2006-04-13
> However I would suggest, that, in addition the login page, a guest clicking on search could get a very short explanation of Googles "site:" syntax.

Im not sure what it shows now, but I would hope it shows some explanation so as to not discourage potential new users. Plus as can be seen throughout many of my posts, discouraging the serch button is never a good idea. So many redundant problems could be avoided if people just searched for the answer, plus they would have it, no need to wait.

Ok, well I'll drop it anyways since it seems that plans have already been made.

---

### Post by trash on 2006-04-15
Would it help to have the default search(which is now set to search all open forums) set to search only one or two of the forums such as the current release 5.10 Gnome/KDE support and maybe instalation/beginer help.
Cafe, backyard, 3rd party projects and many other forums don't need to be included for people not signed in... just a thought.

---

