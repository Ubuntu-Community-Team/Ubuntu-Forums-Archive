---
title: "Running Feisty, using Beryl I installed on Edgy, will it update to Compiz Fusion?"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-04
I installed Beryl on Edgy, and have since upgraded to Feisty (mainly because I wanted to see if the included Compiz was faster than Beryl). Unfortunately, I've been having trouble with the included stuff, so I've stuck with Beryl. 
I would try Compiz Fusion, but I don't want to mess up the Beryl install that I actually have working. So my question is, will the included Compiz and my installed Beryl update to Compiz Fusion...ever? 
Or better yet, would it be safe to try Compiz Fusion? I followed a guide for installing Beryl on Edgy, and I don't have it bookmarked anymore so if I decided I want to go back to Beryl, I have no idea what I'd do.
Can anyone offer any advice?

---

### Post by walkerk on 2007-08-04
This I can help with :)

You're using a Dell w/ ATI correct?

If you have Beryl running you'll have no problems with Compiz Fusion. Before installing Compiz Fusion you need to remove everything Compiz and Beryl related through Synaptic (not including Emerald).. 

Now follow one of this Howto's on installing Compiz Fusion.. I suggest Vorian's..

---

### Post by rainwalker on 2007-08-04
Is it stable/fast?
The main reason I wanted to switch to Compiz is because it's faster than Beryl.

Also, since upgrading to Feisty, I can now do things with Beryl that I couldn't on Edgy (the water effects in particular). Did Feisty unlock some new source of power with my video card?

---

### Post by walkerk on 2007-08-04
> **rainwalker said:**
> Is it stable/fast?
The main reason I wanted to switch to Compiz is because it's faster than Beryl.

Also, since upgrading to Feisty, I can now do things with Beryl that I couldn't on Edgy (the water effects in particular). Did Feisty unlock some new source of power with my video card?

IMO the Compiz Fusion combined the nice look of Beryl/Emerald with the stability of Compiz. Compiz Fusion is incredibly stable on my system (running crappy Intel 945GM).. Much more stable than Beryl.. Since I upgraded, right when Compiz Fusion was available, I've not had 1 crash..

---

### Post by rainwalker on 2007-08-04
It it fast enough for decent day-to-day use?

---

### Post by walkerk on 2007-08-04
> **rainwalker said:**
> It it fast enough for decent day-to-day use?

I wouldn't use it otherwise. :) I can't tell any difference from running metacity or compiz fusion.. 

though its a core2duo & 1gig (but with crappy video)

not sure of your specs.. but a dell inspiron 7000 w/ ati i think you're good.

---

### Post by rainwalker on 2007-08-04
Actually that was my sister's computer, I'm using an Inspiron 8600.

Argg...I want a new computer. You're so lucky!
How well does Ubuntu handle the whole "2 cores" thing? I read something a while back about how software developers were having trouble keeping up with the pace of technology, and were having more and more trouble getting their programs to utilize the full potention of dual-core processors.

---

### Post by walkerk on 2007-08-04
> **rainwalker said:**
> Actually that was my sister's computer, I'm using an Inspiron 8600.

Argg...I want a new computer. You're so lucky!
How well does Ubuntu handle the whole "2 cores" thing? I read something a while back about how software developers were having trouble keeping up with the pace of technology, and were having more and more trouble getting their programs to utilize the full potention of dual-core processors.

7.04 has no issues recognizing both cores. you have to remember though that your two cores will handle seperate processes for the most part. meaning if you only have one program running that uses a lot of the processor it will only use one core. the exception to this is with a program that is multi-threaded.. same deal in every os..

---

### Post by rainwalker on 2007-08-04
Cool!

Okay, so I guess I'll try Compiz Fusion. I'll report back here if I have any trouble

---

### Post by rainwalker on 2007-08-04
Wow, I already have a question...

I'm looking at Vorian's guide at [http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223) and I can see that I'm going to be removing Compiz, but what about Beryl?

---

### Post by walkerk on 2007-08-04
I've seen other that didn't have issues not removing Beryl before installation.. but I did. Without removing Beryl (along with Compiz) my Compiz Fusion took several minutes to load after bootind.. by several I mean 5 or so..

You can try to install Compiz Fusion while keeping Beryl but I honestly don't see the point.

After installing Compiz Fusion you'll be able to have window decorations using Emerald (just like Beryl) by using the following command:

```
compiz --replace -c emerald &
```

to load Compiz Fusion at boot add this to System>Preferences>Sessions:
```
Name: Compiz Fusion
Command: compiz --replace -c emerald &
```

---

### Post by rainwalker on 2007-08-04
Whoa.
I just thought of something; I probably should have desktop effects (Beryl) running while I do this, should I?

---

### Post by rainwalker on 2007-08-04
Oy vey, I have to go mow the yard so I'll be back in a little while.

Thanks for all of your help so far :)

---

### Post by rainwalker on 2007-08-04
YAY!
Okay, so I have it running and it works and all that, but how do I 
1. Change the theme
2. Get 4 workspaces instead of 3
3. I'm having trouble setting the Tabbing bindings

---

### Post by bruckwine on 2007-08-04
Hi - new here but loving feisty! Such a difference compared to XP esp with Beryl...i tried to install compiz fusion first )of course0 but all I got was the borderless windows and chaos..uninstalled it and tried beryl - worked instantly :D..now I'm wondering if I should try again but w/o removing beryl (so that I can fall back on it)...same problem as the OP I guess. Perhaps I need a new PC (using a Dell 2200 w intel 915GM graphix)?!

---

### Post by ScottFW on 2007-08-04
With compiz fusion I use Emerald as my window decorator, just like I did with Beryl. So I change themes the same way I did with Beryl.

You have 3 workspaces, meaning your cube is really a triangle? In the compiz config settings manager, go under general options, desktop size, and change "horizontal virtual size" to 4.

Grouping and tabbing... still learning that myself since I just installed compiz fusion yesterday, but if it's not working at all make sure that your "super" (windows) key is functioning, since I think most of the default tab/group bindings use it. I had to tweak my xorg.conf for the super key to work. It sure is nice getting the eye candy back after my Feisty upgrade borked Beryl!

---

### Post by rainwalker on 2007-08-04
I'm still working on the theme, but I did figure out the workspaces thing.
The tabbing is working fine, it's just confusing!

Feisty didn't mess up my Beryl at all, in fact, it somehow made it better!
1. It runs a little faster than on Edgy
2. I can now use the water effects

Compiz never worked, even the included Compiz in Feisty. 
Fusion is the only thing besides Beryl to actually work, I'm so happy!

---

### Post by rainwalker on 2007-08-05
Nevermind, it's stopped working.

walkerk, I put that command you said in the startup programs thing and restarted, and now Fusion doesn't work.
I made a thread about it here:
[http://ubuntuforums.org/showthread.php?p=3135440](http://ubuntuforums.org/showthread.php?p=3135440)

---

