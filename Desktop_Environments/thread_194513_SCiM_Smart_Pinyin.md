---
title: "SCiM Smart Pinyin"
date: 2006-06-11
forum: Desktop Environments
---

### Post by polt on 2006-06-11
I just upgraded to 6.06 and reactivated my SCiM for entering Chinese characters.  However, there is now no option to input "Smart Pinyin" as there was before.  Anyone else had this problem?  Any ideas what's wrong?  Thanks a bunch for any help!

---

### Post by polt on 2006-06-11
Here is some follow up info.  If I go into SCiM setup > Generic Table > Table Management, there is no table for Mandarin Pinyin or Smart Pinyin.  I suppose I could install the pinyin table if I had one, but there doesn't seem to be one in the set of Chinese input tools installed on my computer.  

SCiM now has a scim-pinyin module.  So maybe there is a different way to input pinyin now.  I can't tell.

---

### Post by polt on 2006-06-11
Gar, I figured it out, it was just a matter of I can't read Chinese characters that well yet.  So, If you look at the input methods under Chinese Simplified, there is one that is described completely in Hanzi.  That one, more or less says "pinyin".  So If anyone else is having this problem, that is your solution. ;)

Oh, and if you don't see the option in chinese characters, try downloading "scim-pinyin", then check.

---

### Post by octathlon on 2006-07-11
I'm not getting it. I just installed Dapper and can't find Pinyin input either.  I went to Table Management, but I can't find the one you mean.  Synaptic says I have the scim-Pinyin installed. 

The only tables I have listed under Simplified are Erbi, Erbi-QS, Wubi, and Ziranma. No idea what those are.  Can you help?
Thanks

PS. Actually I now seem to have the problem that gedit freezes whenever I try to pick SCIM so it's worse than I thought.:(

---

### Post by octathlon on 2006-07-11
OK, I found the right one to use for pinyin input, and I started it in gedit. The problem is, it keeps freezing up, then I have to force gedit to close, then when I try to start it again, nothing happens.  I have to reboot. Hey, this reminds my of that other OS.
Have you had this problem?  What programs do you use scim in?

---

### Post by elfgoh on 2006-07-12
Hi I used scim in gedit without problems. Is there any way for me to use in FF?

---

### Post by tonyutada on 2006-09-14
Hi

I have the same problem as octathlon. The smart pinyin is not under IMEngine's global setup. no pinyin table as well.

Synaptic manager shows the pinyin is installed.

To my surprise, in Synaptic manager UI I found the scim+smart pinyin, two scim icon show up. But after I close the Synaptic, only one scim exists, no smart pinyin any more.

[IMG]http://picasaweb.google.com/Tonyutada/Temp/photo#4974820158935859218[/IMG]

---

### Post by the lush on 2006-09-19
OK, I have managed to get Scim up and running, but I have a problem; how can I use Hanyu Pinyin to input Traditional characters? I have no use for simplified, but no desire to try and learn a new keyboard layout to use Zhuyin.

Also, what is the Chewing input method. I set the keyboard layout to Hanyu Pinyin under Chewing, but can't work outhow to actually input any meaningful characters.

This is a real deal breaker for linux and me, if I can't type Chinese I will have no choice but to return to Windows, and after the amount of effort put into this so far, I am loathe to do that.

Thanks in advance for any help.

---

### Post by Abiezer on 2006-09-19
I use SCIM pinyin (on the menu as &#26234;&#33021;&#25340;&#38899;) for entering Chinese, and find that it offers you the choice of both simplified and full-form characters, it's just that the full-form is listed later in the list of options it offers.
For example, if I try 'rang', simplified &#35753; is option 1 on the list of possible characters, full-form &#35731; is option 5.

---

### Post by the lush on 2006-09-19
While that would work, it would be very time consuming. I also find that I need to select the character each time with scim, it is not predictive, so I have to type the pinyin, select the character, then type the next piece. Is it possible to have it correct on the fly?

---

### Post by Abiezer on 2006-09-19
I find that it learns words (i.e. two character combinations), including compounds of full-form charcters, (I just taught it &#35731;&#20301; as a test), but after a poke about [the SCIM homepage]("http://www.scim-im.org") I'm afraid you're right about not being able to choose full-form charcters as default with pinyin input, which I'd like too.
If I find a solution I'll post it here.

---

### Post by brightnemo on 2006-09-19
I'm a scim user myself, but for simplified chinese.

I've made some test but I wasn't able to find a solution to your problem, why don't you ask the wise opinion of our friends in the chinese forum? for sure they will have a much greater understanding of the problem....

---

### Post by the lush on 2006-09-29
> **brightnemo said:**
> I'm a scim user myself, but for simplified chinese.

I've made some test but I wasn't able to find a solution to your problem, why don't you ask the wise opinion of our friends in the chinese forum? for sure they will have a much greater understanding of the problem....

I thought of this, but I assumed that most people wanting to use traditional characters would be using Zhuyin for entry anyway, so would not have encountered the problem, whereas most people who want to use Pinyin will be using simplified characters. The problem only arises because I want to use Pinyin for traditional characters in the same manner as the MS2002 IME allows. I'll follow up on your suggestion just in case. Thanks.

---

### Post by rykel on 2006-12-24
hi,

i am very glad to find a thread dealing with scim and chinese...

ever since i upgraded to edgy eft, i have NOT been able to even set up scim-pinyin properly... i used to get scim loaded at bootup automatically simply be installing Chinese in System/Administration/Language Support but not in edgy anymore...

are you able to teach me how to set up scim to auto-start at bootup? (maybe a line in Sessions/Startup Programs if i recall correctly)

thank you!!

---

### Post by polt on 2006-12-31
As far as getting scim to start up with the computer, all you have to do is go to System -> Preferences -> Sessions.  Under "Startup Programs", add a command that says "scim -d".  Restart gnome panel, or just restart the computer, and it will startup.  However, in Edgy I still haven't been able to enable the Chinese input by using the hotkey.  It isn't working for some reason.  Still working on that one.  Good luck!

---

### Post by asantainnasa on 2007-01-05
hi, i'm kinda new to ubuntu, directed here by a friend
i'm using 6.10 edgy
i installed language support for chinese
and i set up the smart pinyin in SCIM configuration
but none of my trigers seem to work
when i manually start scim, a icon appears in the taskbar, and when i click on it nothing happens, and even now the triggers for switching mode doesn't work
am i doing something wrong? :(
any help would be appreciated

---

### Post by dl7und on 2007-03-01
I'm not sure if you did something wrong and don't completely understand what you did, but... I noticed that the way to activate scim seems to have changed in 6.10. After installing scim, you should open a terminal and type
```
im-switch -s scim
```
That way, scim gets set up as input method for that account. Maybe that can solve some of your problems.

---

### Post by asantainnasa on 2007-03-03
thanks! everything solved =]

---

### Post by oldHat on 2007-05-06
I had this working fine under Fedora, and I'm sure everything was fine when I started out with Ubuntu, but I'm having trouble with Smart Pinyin now.  

The menu bar is suddenly in Chinese, and I'd really prefer to see it in English.  Any advice?  I'm a native English speaker, studying Chinese, so this is not much use to me like this.

When I want to type "&#20154;" I key "RE", then the only choices I'm given are:  &#28909; &#24825; &#21903; &#29105; &#28163;   My input method looks like &#26234;&#33021;&#25340;&#38899;

Today, tried re-installing with Synaptic.  It's still the same.

My 2 goals are to get the Scim display to show up in English again, and to re-enable Smart Pinyin.  It might turn out to be easier to learn Zhuyin.

---

### Post by asantainnasa on 2007-05-06
> **oldHat said:**
> When I want to type "&#20154;" I key "RE", then the only choices I'm given are:  &#28909; &#24825; &#21903; &#29105; &#28163;   My input method looks like &#26234;&#33021;&#25340;&#38899;


There's nothing wrong with your SCIM, the correct spelling for that would be "ren" instead of "re", and &#26234;&#33021;&#25340;&#38899; is the best

---

### Post by oldHat on 2007-05-07
> **asantainnasa said:**
> There's nothing wrong with your SCIM, the correct spelling for that would be "ren" instead of "re", and &#26234;&#33021;&#25340;&#38899; is the best

That doesn't help me at all.  "REN" is not a recognized keystroke sequence.

If I was able to type "REN", I wouldn't be looking for help here.  I'm stuck by the second keystroke; I don't get the opportunity to enter the 3rd character.  

SCIM only allows me two keystrokes.  Keystroke #1 is 'R'.  Keystroke #2 is 'E'.  After that, I have a choice of those 5 characters.  REN isn't one of them.  If I insist on typing keystroke #3, it just gives me one of those 5, then  treats the N as the first character of the next word.  

If I can get my input bar back to English, then maybe I'll be able to switch back to smart pinyin.

Now that I think about it, my problem could have started when I added the US International keyboard layout as my secondary layout.  Unfortunately, dropping it doesn't seem to help.

---

### Post by Abiezer on 2007-05-15
Following up on my earlier post that you can't select full or simplified input under SCIM, I learn from fellow forum user jiawen this isn't true.
When you have the SCIM entry menu brought up, you can hit control + forward slash (Ctrl and /) to cycle through options. You'll see the character &#20013; on the menu change to &#33521; for English, then &#31616; for simplified then finally &#32321; for full-form traditional characters. Thanks jiawen!

---

### Post by Jiawen on 2007-05-15
No problem! Good to know I'm helping. :)

---

### Post by oldHat on 2007-05-18
> **polt said:**
> Gar, I figured it out, it was just a matter of I can't read Chinese characters that well yet.  So, If you look at the input methods under Chinese Simplified, there is one that is described completely in Hanzi.  That one, more or less says "pinyin".  So If anyone else is having this problem, that is your solution. ;)

Oh, and if you don't see the option in chinese characters, try downloading "scim-pinyin", then check.

My problem was similar.  I seem to have got it solved now.  I can finally produce the "&#20154;" character with SCIM!  My problem also was that I don't read Hanzi well enough to navigate the menus.  Basically, I just had to pick &#26234;&#33021;&#25340;&#38899; &#65292; &#20840;&#65292;&#31616;

---

### Post by skeelee on 2008-02-11
Hi, polt,

Came to this thread because of similar problem of missing Smart Pinyin in SCIM.
After searching through the net, found a solution that works (but now couldn't find the site to post a reference here).

The solution:
1. Use Synaptic to remove SCIM completely.
2. Remove previously installed SCIM files/data using terminal thus:
    sudo rm -rf /etc/scim
    sudo rm ~/.scim
    sudo rm /root/.scim
3. Reinstall SCIM through System - Administration - Language Support.

Just in case you still need the solution.

---

