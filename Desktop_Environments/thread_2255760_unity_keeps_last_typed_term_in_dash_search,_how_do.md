---
title: "unity keeps last typed term in dash search, how do I stop this?"
date: 2014-12-07
forum: Desktop Environments
---

### Post by DigitalGrinch on 2014-12-07
Getting really annoyed with certain behavior of unity. 
When I click on dash home to search for an application, the previously searched term remains, even after I have started original application and the dash menu closes.
The next time I click dash, it has the same term I previously searched for. 

This is incredibly annoying, how do I fix this? 
I would like to remain using unity, if possible. I like both GNOME and KDE, but I find I have better luck finding guides/howtos/help when I stick with Unity as that is what the majority of Ubuntu users use

I searched google and this forum. If this is a double post, please forgive me, I did not know what to search for to find solution

---

### Post by ajgreeny on 2014-12-07
Here you go!
[http://askubuntu.com/questions/455524/how-to-turn-off-dash-history-from-previous-searches-in-ubuntu-14-04](http://askubuntu.com/questions/455524/how-to-turn-off-dash-history-from-previous-searches-in-ubuntu-14-04)

I found this easily with a search on my own custom google ubuntu-search site.  [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao)
Searching ubuntu related answers using this is very much more effective that general google and easier than a search of this forum.  Bookmark it for future if you wish to; it is available to all.

---

### Post by deadflowr on 2014-12-07
I think the OP wants to set the dash to clear on exit.
So when you start to dash the search field is empty.

I have no idea, nor do I really care about, how to fix it.
I would suggest file a bug report, detailing just that.
I would not expect it to be fixed in already released versions, but maybe for future releases like 15.04.

The privacy setting only allow you to clear your searches history, but not the actual search field.

Maybe suggest in a bug report to allow search field to always start empty.

It's never bothered me because when I open the dash if the field is full, simply typing anything new will override the old info.
Hitting the spacebar clears the field as well.
But I can see how it would bother others.

Of course the other option would be to dig through source and see if you could add the option, but who'd want to do that anyway.

---

### Post by DigitalGrinch on 2014-12-07
> **ajgreeny said:**
> Here you go!
[http://askubuntu.com/questions/455524/how-to-turn-off-dash-history-from-previous-searches-in-ubuntu-14-04](http://askubuntu.com/questions/455524/how-to-turn-off-dash-history-from-previous-searches-in-ubuntu-14-04)

I found this easily with a search on my own custom google ubuntu-search site. [https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao)
Searching ubuntu related answers using this is very much more effective that general google and easier than a search of this forum. Bookmark it for future if you wish to; it is available to all.

Thank for for the response, but as stated by respondent below, this does not solve my issue. I'd like Dash search to be empty each time.

> **deadflowr said:**
> I think the OP wants to set the dash to clear on exit.
So when you start to dash the search field is empty.

I have no idea, nor do I really care about, how to fix it.
I would suggest file a bug report, detailing just that.
I would not expect it to be fixed in already released versions, but maybe for future releases like 15.04.

The privacy setting only allow you to clear your searches history, but not the actual search field.

Maybe suggest in a bug report to allow search field to always start empty.

It's never bothered me because when I open the dash if the field is full, simply typing anything new will override the old info.
Hitting the spacebar clears the field as well.
But I can see how it would bother others.

Of course the other option would be to dig through source and see if you could add the option, but who'd want to do that anyway.

Thank you for the response. I will wait to see if someone has an answer on how to fix or configure this myself. If no answers come, I will file a bug report. Is the proper place to file the report here? [https://bugs.launchpad.net/unity](https://bugs.launchpad.net/unity)

---

### Post by mc4man on 2014-12-08
Wells that's the place but I'm pretty sure this is the intended behavior & really not that big of a deal at all  as it has value
You can reuse the last search term per lens or as soon as anything is typed the previous disappears as it is preselected.
The current behavior is the result of [a bug quite some time ago]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/826904") when previous term remained but then had to be removed [so the fix to make it selected ]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/oneiric/unity/oneiric/revision/105#plugins/unityshell/src/DashView.cpp")indicates that it's desired to have it when reopening 
(- otherwise the bug could have been fixed by clearing on close or re-open

---

### Post by DigitalGrinch on 2014-12-17
Made a bug report. 
Something tells me I'll be moving to GNOME desktop soon

---

### Post by buzzingrobot on 2014-12-18
> **DigitalGrinch said:**
> Made a bug report. 
Something tells me I'll be moving to GNOME desktop soon

Is this a privacy concern? 

Gnome search does not remember the previous search term.  But, there are occasions when someone might wish it did.  The previous search term in Unity is immediately deleted once you begin to type something. E.g., if the previous term was "dog", then typing the "c" in "cat" will blank the field and enter the "c".

KDE, by default, does not rely on search to find apps, files, etc., but uses a traditional menu system.  However, the Kicker widget can be added to provide similar functionality. Recent releases include the rewritten/redesigned desktop search capability which, in my experience, is excellent.

---

