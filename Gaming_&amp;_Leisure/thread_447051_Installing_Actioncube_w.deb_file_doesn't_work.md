---
title: "Installing Actioncube w/.deb file doesn't work ?"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by Sweet Spot on 2007-05-17
Hey guys. Please help me a bit here. Last night I downloaded a few games which seem to be really good/cool, and I'm pleased with them for what they are, considering the price ! Amongst those I downloaded from Getdeb.net is Actioncube. But I saw two files:

1)actioncubedata_0.92-0~getdeb1_all.deb
and 
2) actioncube_0.92-0~getdeb1_i386.deb

I clicked on the first one, as it's a much larger file, and when it was done, it said succeeded installing. But, I couldn't find it on the games list. So I clicked the second one, and got the message:"Error. Dependency is not satisfiable: libc6"

I just got home, and was about to start fresh, so I attempted to "purge" actioncube all together, but when I tried, I got a message saying it couldn't find it. But it must be installed somewhere, because when I clicked on the first file again, the button which has a check to download was marked : "reinstall package".

Basically, how should I get rid of those files/packages and how should I go about trying to install it again ? I'd really appreciate help w/this. Thanks.

doug


P.S. While I'm at it, perhaps I should ask about what to do with the Tremulousx86.run file ? I've no idea as to how to install that game at all. At least with the .deb's, I know that it technically SHOULD work just by clicking on them.

---

### Post by earobinson on 2007-05-17
where did you get the debs from [http://www.getdeb.net/](http://www.getdeb.net/) worked for me, also double click the debs and use the gnome deb installer that way it will auto install dependencies.

---

### Post by Sweet Spot on 2007-05-17
> **earobinson said:**
> where did you get the debs from [http://www.getdeb.net/](http://www.getdeb.net/) worked for me, also double click the debs and use the gnome deb installer that way it will auto install dependencies.

I did. I'm actually on getdeb.net right now making sure there was nothing I missed. You do see that there are two files though, right ? One says "actioncube" and is 260.9 Kb and the other is "actioncube-data" and is 17.7 Mb.  Initially, I clicked on the 17.7 Mb one, and it said it installed, but it's nowhere to be found, and I can't uninstall it either at this point. And then, as I said before, I tried the other one, but got that error message.

Edit: Perhaps I don't have a specific repository ? I think right now I"m using all of the standard ones plus Universe and such...

---

### Post by DoktorSeven on 2007-05-17
The two files are certainly both required, as is the case for many games, it divides the game data from the actual executable (so if the exectuable has to be updated, you don't have to get the data again if it doesn't change).

---

### Post by Sweet Spot on 2007-05-17
Then should it have mattered which .deb I clicked on first ?  The smaller file, when I click on it gives me that error message saying that dependencies aren't satisfiable. What to do about that then ? 

Doug

Edit: Looking in /usr/share/games, I definitely see the actioncube folder and the data contents, so that part was surely installed. But this thing with not satisfying dependencies... must be screwing up the rest of it.

---

### Post by DoktorSeven on 2007-05-17
I just installed it myself (data package first) out of curiosity and didn't have any trouble with dependencies.  If you're running an older version of Ubuntu (your information says 6.06) it's possible that this package was built for a later version so it has some odd dependency that only a later version of Ubuntu can satisfy.

If you have the second (data) version installed and want to get rid of it, it should be called "actioncube-data", **sudo apt-get remove actioncube-data** should get rid of it.

---

### Post by Sweet Spot on 2007-05-17
Strange. That command worked, whilst "sudo apt-get remove --purge"  did not. I wonder why ?   

About possibly needing a dependency which falls out of the range of Dapper, that's pretty annoying. If Dapper is supposed to be LTS first of all, and all the other versions are still not formally released, then why would devs want to break dependencies like that ?   

They should understand that even with the advent of a new release, not everybody wants up upgrade automatically. I'm sticking with the "If it ain't broke, don't fix it" credo for the time being. I just don't have the time right now to TEST out a new version of Ubuntu, even if a million people say that it's stable. 

I think this also sends a mixed message to people whom may be thinking about switching over from Windows. It's entirely confusing actually, and this area (games) isn't the only place where this behavior is seen. Now, I may be assuming a whole lot, by saying that this is indeed the case, but if it is, I stand by my words. If there's another explanation for why I'm having this problem, I'd love to see it documented, so that I don't have to run in circles. 

I can't be the only person having this problem, surely ? (Why yes you are, and don't call me Shirley !) :) 

Also, on the debget.net page, if you click on the link next to the actioncube screen shot, it links you to another page which on the bottom of it, has links to feisty, edgy and dapper. Unfortunately, they all link directly back to the page which you JUST came from ..... So it's an endless circle ... With no valid download links as far as I can tell.

---

### Post by DoktorSeven on 2007-05-18
1) Getdeb is, from what I understand, independent of Ubuntu; on their "About" page they state:

> Note: The GetDeb team may not follow the Debian/Ubuntu packagning guidelines meaning you should not expect the same level of quality control as you get from those. On the other hand you will be able to get usefull packages that will hardly get into Debian/Ubuntu due to policy constraints.

So don't expect them to work things just like the official Ubuntu repos.  If someone packages a program specifically for a certain release, there's not much you can do about it except try to get someone to build a Dapper package, or build it from source yourself.  

2) Not sure why they have links to Dapper/Edgy with no downloads on them (I assume this means there are no packages avaiilable; it would be easier to simply remove those links, I think).  Clicking the Feisty links take you to a page with downloads.

I'm sure in this case it's simply that no one that uses Dapper has taken the time to make a package for it.

---

### Post by Sweet Spot on 2007-05-18
Yep, seems to be what I was thinking too. 

Thanks for taking the time out though, to try and help me, I do appreciate it. 

I wonder if I'll be able to install it with the tar.gz file I have at some point though. 

Doug

---

