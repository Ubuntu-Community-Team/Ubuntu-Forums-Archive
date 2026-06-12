---
title: "Firefox no fonts mystery in other user accounts"
date: 2009-03-28
forum: Desktop Environments
---

### Post by nanonils on 2009-03-28
I'm pulling my hair - only I have normal font rendering in Firefox 3.0.7, 32bit Jaunty beta and Opera 9.64 but not the other two users. I have convinced my wife to use Ubuntu and now she's back using the Vista partition on my laptop till hers with Ubuntu only is fixed...

Both my wife and I have administrator access and the 3rd user is a desktop user. 

My problems (already present before upgrading to Jaunty): 
1. some fonts don't show at all in FF in two accounts but are OK in mine
2. Opera does show the same pages but the font is extremely pixelated only in those two accounts but not in mine and the rendering it very hard to read under time pressure (my wife's exam preparations).

Attached: 
1. snapshot of a exam preparation web site in FF and Opera showing no fonts and screwed up fonts, respectively
2. snapshot of Ubuntuforum.org web page showing no fonts for subforums

What I tried so far:
1. confirmed correct font location in /usr/local/share/fonts - I had installed MS core fonts including Vista true type so Powerpoint presentations have the same font on all machines and they are all in this folder. 
2. confirmed same standard font selection for all browsers and all users as Arial
3. upgrade to Jaunty

Thank you for your help!

---

### Post by nanonils on 2009-03-28
Holy ****! One word: permissions!

After re-reading my post I figured I better check file permissions... 

Of course all the good MS fonts that I copied from my Vista partition and spread to my other computers had me as the sole owner and the only one with access permission. I still don't get why a non-proprietary font such as Arial would not render in Opera but perhaps what happened was that when I copied all the fonts I chose to replace all duplicates and now even Ubuntu standard fonts had me as the sole one with access.

If someone reads this who screwed up fonts in a similar way, here is how you can batch change permissions: 
1. open a console and type in for root access: sudo nautilus
2. go to usr/share/fonts and select this folder
3. right click and go to Permission
4. choose Others folder access: access files

Hit the big button lower left in this window to apply to all files in this folder and subfolders.

I guess 18 years of MS Windows and FAT file systems have fried my brain. Sometimes it helps to just write things out, post them for public shaming and you start to think in a more critical way...

---

### Post by aeklabunde on 2009-04-24
I had the exact same issue with Hardy Heron. Only, I changed the permissions to the fonts folder and the problem persisted --each font in the folder still had its own restrictive permission.  So I selected all the fonts and right clicked then selected Properties, then Permissions and then allowed Others access. I did this for both usr/share/fonts and etc/fonts and all works great now.  Hope this helps anyone else still using Hardy Heron!

---

