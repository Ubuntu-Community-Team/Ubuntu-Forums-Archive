---
title: "How to switch off fade effect when prompted for password"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Raptor Ramjet on 2006-06-27
Since the upgrade to 6.06 whenever I am required to input my password the expected "prompt for password" dialogue appears as normal but it's had a "fade in" effect added to it.

I am therefore wondering if it's possible for me to switch off this fading effect ? as it looks really shoddy on my set up (I have a low end GPU) and I must confess that, as I do with most such gimmicky effects, I find it unnecessary and somewhat irritating.

Thankyou.

---

### Post by videodrome on 2006-07-31
Bump this. Anyone?

---

### Post by adamkane on 2006-07-31
I despise the fade effect as well. It's too choppy on my PC. Apparently it's necessary:
[http://www.ubuntuforums.org/showthread.php?t=68287](http://www.ubuntuforums.org/showthread.php?t=68287)

---

### Post by xenon2000 on 2006-08-15
[http://ubuntuforums.org/showthread.php?t=235560&highlight=fade](http://ubuntuforums.org/showthread.php?t=235560&highlight=fade)

I too am looking for a solution to this. As you mentioned, it wasn't this way before. And a fade effect is NOT required for security people. Go ahead and disable interaction with other windows etc if needed for security, but give us a way to disable such silly effects. I have plenty of speed, but I don't need this effect and it's annoying.

I use Xubuntu 6.06 XFce desktop, no Gnome desktop dependencies installed, etc.

---

### Post by orb9220 on 2006-08-15
Well if it is a app on your panel. Like I have a gksudo nautilus icon on a panel. If I change the command from: gksudo nautilus to:

gksudo -g nautilus then the fade dosn't happen I think it's called the grab function.

---

### Post by xenon2000 on 2006-08-15
> **orb9220 said:**
> Well if it is a app on your panel. Like I have a gksudo nautilus icon on a panel. If I change the command from: gksudo nautilus to:

gksudo -g nautilus then the fade dosn't happen I think it's called the grab function.

I forgot to post this thread here... I made a comment on -g

[http://ubuntuforums.org/showthread.php?p=1383774#post1383774](http://ubuntuforums.org/showthread.php?p=1383774#post1383774)

Here is one of my posts from the thread above.

-g is --disable-grab

And I thought --disable-grab defeats the security of pausing all applications to prevent possibly grabbing the password as you type or capturing the screen.

If this is so, then -g in unacceptable and the fade effect needs to be controllable by itself as an effect and not just simply disable the event that is tied to the effect.

---

### Post by orb9220 on 2006-08-15
Ahhh Point taken. But if that is a cocern I would have to ask myself is my system really secure? How did a sniffer program got on my system to capture  in the first place. And if my system is truly secured and setup proper than  I personally not that much concerned about the -g option.

Yes the die-hards will scold me but to rid myself of annoying things that take away my experence with ubuntu I am willing to take teeny-tiny chances.

---

### Post by xenon2000 on 2006-08-16
Yes, there are many other security issues that are much higher than using -g and if you want to use that, ok.

But I am unwilling to trade an annoying fade effect for an openly known security downgrade. 

I just don't understand why the fade effect was hard coded to the function like it is. No excuse for that. They can have the exact same "lock out" feature without faded out the rest of the screen and so I don't know why they tied it directly like they did.

Having threads like this for future searching history is a great thing. And is another reason I posted my feelings on using -g , people can now choose to use this method and also know the details of using it.

Hopefully a better solution becomes available in Edgy Eft, but somehow I doubt it.

---

### Post by orb9220 on 2006-08-16
Good point I guess the coders thought it was cool for what ever reason. The reason it's such a peave with me is I work most at night in a darken room.  

Yes I am a Night Creature.

So that darkening effect determines if I can see the keyboard or not. It may be trivial but it's annoying enough to me anyways.

The other one I think is silly is not to display the password to let me  see I am entering the right password. Which on multiple systems and in a hurry I catch myself typing the wrong one.

And I know atleast 50 people that find this kind of thing annoying like really most people are alone when they type in thier password.

What is the point. At least give the option to show or hide password entry

---

### Post by xenon2000 on 2006-08-16
> **orb9220 said:**
> ... I work most at night in a darken room.  


[http://www.crazypc.com/products/4184.html](http://www.crazypc.com/products/4184.html)   This is a cool USB backlit keyboard that you can change the color on the fly, lights the characters and inbetween keys... though I haven't tried  it, so if the color change is via software we are most likely out of luck. But it does state brightness is a hard control. Also has multimedia keys and volume knob, but not sure if that would work in Ubuntu either. Newegg also has the Eclipse 1 with just blue light that has been reported to work perfectly under Gentoo Linux. [http://www.newegg.com/Product/Product.asp?Item=N82E16823175103](http://www.newegg.com/Product/Product.asp?Item=N82E16823175103)

> **orb9220 said:**
>  The other one I think is silly is not to display the password to let me  see I am entering the right password. Which on multiple systems and in a hurry I catch myself typing the wrong one.

And I know atleast 50 people that find this kind of thing annoying like really most people are alone when they type in thier password.

What is the point. At least give the option to show or hide password entry

I agree with both sides of this arguement. At home, I want to see my password, at work I don't want to see my password. I think both methods have their place.

I completely agree with you, it should be an option. And it should be a system wide option.

---

### Post by stvmty on 2006-08-20
Just wanted to add, that fade effect looks awful with compiz-xgl enabled.

---

### Post by antiplex on 2007-04-10
anybody found a solution for this in the meanwhile?
that fading effect really looks stoopid and even more stupid with xgl + berly / compiz . i'd really like to simply darken the background in like one step instead of fading in like 20 steps or so...

---

### Post by xenon2000 on 2007-04-10
> **antiplex said:**
> anybody found a solution for this in the meanwhile?
that fading effect really looks stoopid and even more stupid with xgl + berly / compiz . i'd really like to simply darken the background in like one step instead of fading in like 20 steps or so...

Currently you can't do that. It's hard coded. Now if someone wanted to customize the code for all of us, that would be great. But in the meantime, the only solution isn't really a solution, but a piss poor work around. You disable the security feature associated with the fade effect. Which is posted on page 1 of this thread.

Hopefully by the next release of ubuntu they will fix this. Unfortunately I don't think any of the Ubuntu team thinks this is an issue and it most likely will never be fixed by the Ubuntu team. More likely is that if a fix comes along, it will be from an outsider who loves code and linux. I can only hope then see this thread.

---

### Post by ardchoille42 on 2007-04-10
> **Raptor Ramjet said:**
> Since the upgrade to 6.06 whenever I am required to input my password the expected "prompt for password" dialogue appears as normal but it's had a "fade in" effect added to it.

I am therefore wondering if it's possible for me to switch off this fading effect ? as it looks really shoddy on my set up (I have a low end GPU) and I must confess that, as I do with most such gimmicky effects, I find it unnecessary and somewhat irritating.

Thankyou.

Do you know what that "fade effect" is actually doing? When that fade effect activates, it is actually a security feature that is keeping anyother apps from grabbing the admin password. If you have a key logger or mouse mapper running to grab the admin password, the fade effect is preventing those apps from grabbing the admin password, and thus keeping your admin password safe. It's a security feature and, just my opinion, should not be disabled.

---

### Post by xenon2000 on 2007-04-10
> **ardchoille42 said:**
> Do you know what that "fade effect" is actually doing? When that fade effect activates, it is actually a security feature that is keeping anyother apps from grabbing the admin password. If you have a key logger or mouse mapper running to grab the admin password, the fade effect is preventing those apps from grabbing the admin password, and thus keeping your admin password safe. It's a security feature and, just my opinion, should not be disabled.

I agree, it should not be disabled. All this has already been covered and said on page 1 for those who are not reading the start of this thread.

But the fade is unnessessary. Vista does the exact same thing for security, but from what I can tell, it's instantly 1 step and not a "fade" transition. So it's near instant and not nearly as annoying as this Linux implimentation. This is not an invitation to bash Windows. Just saying that if this security feature in Linux would just lose the whole fade effect and instead just instantly switch to dark using 1 step instead of a fade transition. It would be faster, VNC friendly and less annoying.

---

### Post by ardchoille42 on 2007-04-10
> **xenon2000 said:**
> ..Just saying that if this security feature in Linux would just lose the whole fade effect and instead just instantly switch to dark using 1 step instead of a fade transition. It would be faster, VNC friendly and less annoying.

Good point.

---

### Post by antiplex on 2007-04-10
ok, i guess i got to live with that for now...
thanks for pointing out that it's a security feature (i wouldn't want to turn that off), i just hope that in the future security and eyecandy will be split apart for those who wish to do so :wink:

---

### Post by Ramses de Norre on 2007-04-10
Fort hose who didn't know, you can set gksudo to not use grab by default:
```
gconf-editor /apps/gksu
``` and set disable-grab to true.

---

### Post by xenon2000 on 2007-04-11
> **Ramses de Norre said:**
> Fort hose who didn't know, you can set gksudo to not use grab by default:
```
gconf-editor /apps/gksu
``` and set disable-grab to true.

Come on people, "for those who don't know" ALL of this has already been discussed on page 1 of this thread. Why do people search for answers and then not even READ the start of the thread... at least page 1, this isn't a huge 10+ page thread people. 

Everything is covered in much detail on page 1. Not much reading at all. And so far, all of page 2 is just a repeat of page 1. Very sad people.

---

### Post by Ramses de Norre on 2007-04-11
> **xenon2000 said:**
> Come on people, "for those who don't know" ALL of this has already been discussed on page 1 of this thread. Why do people search for answers and then not even READ the start of the thread... at least page 1, this isn't a huge 10+ page thread people. 

Everything is covered in much detail on page 1. Not much reading at all. And so far, all of page 2 is just a repeat of page 1. Very sad people.

I didn't had the time or interest to read through the whole thread and thought my addition could be useful, I did a search through the thread for "gconf" with firefox and didn't find any occurrence.
Sorry if I was too helpful to you.

---

### Post by xenon2000 on 2007-04-11
> **Ramses de Norre said:**
> I didn't had the time or interest to read through the whole thread and thought my addition could be useful, I did a search through the thread for "gconf" with firefox and didn't find any occurrence.
Sorry if I was too helpful to you.

Half way down on page 1 (not much reading), I myself describe the -g option to disable grabbing the screen.

I also link to this thread below, which has 3 pages, but mostly only page 1 is of any use...

[http://ubuntuforums.org/showthread.php?t=235560&highlight=fade](http://ubuntuforums.org/showthread.php?t=235560&highlight=fade) 

....and it's page 1 is basically the same as page 1 on this thread. I only cross linked them because they both existed.

You don't need to apologize for trying to be helpful. And I am not just commenting at you. But everyone posting in page 2 so far... the posts are small on page 1, and I am saying it's sad that people can't at least read page 1 before posting. 

It's not that hard. And it really does not take much time at all. I mean really people, it would barely cover 1 printed page in a youth novel. (And no, I don't read Harry Potter, in which I am implying.)

---

### Post by xenon2000 on 2007-04-11
CRAP, now a useless page 3 !!!

---

### Post by hihihi on 2007-05-06
page 4 will be great.

good that someone points out security-risk.thx

---

