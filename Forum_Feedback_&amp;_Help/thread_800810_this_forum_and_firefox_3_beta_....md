---
title: "this forum and firefox 3 beta ..."
date: 2008-05-20
forum: Forum Feedback &amp; Help
---

### Post by Fizz_sweden on 2008-05-20
Hi everyone!

Im new to ubuntu (tried to use a few different linux releases like  six years ago though, which failed because of non supported hardware), and installed 8.04 on my laptop.

Im absolutely thrilled about the userfriendliness and ease of installation (etc. etc. etc. :)), and has hardly used Win since, although i keep a partition for gameplay reasons.

Today i tried to register on this very forum, and discovered that the reCAPCHA security image doesnt seem to work in the bundled Firefox 3 beta .... 

Ok, i restarted and registered using Win. Restarted again, and tried to login. I enter my username and password and the forum greets me, and send me to the forum main page, but im still not logged in ... As soon as i try to post the forum asks for my user and password ... (Which means that im writing this on Windows Vista) ... 

I feel a bit stupid right now, like theres something simple ive missed, or is it a fact that the ubuntu forum dont support the webbrowser supplied in the lastest ubuntu release?

---

### Post by Joeb454 on 2008-05-20
It does support it, I don't know why you're having issues (Typing this from Firefox 3 on 8.04 right now).

Can you not log in either? After it asks for your username and password that is? Also try clicking "remember me"

---

### Post by ad_267 on 2008-05-20
Hmm I just logged out and the Captcha image works for me on Firefox 3. I also have no problem logging in. I'm not sure why you'd be having these problems. Do you have cookies enabled?

---

### Post by kestrel1 on 2008-05-20
The beta version of FF3 is a bit buggy. You could remove that & install FF2 instead. I had issues with FF3 & am now using FF2 with no problems.
To remove FF3:
```
sudo apt-get remove firefox
```
& to install FF2:
```
sudo apt-get install firefox-2
```
Do the above from a terminal.
Hope that helps.

---

### Post by Fizz_sweden on 2008-05-20
thanks for the quick reply!

i´ve tried to log in multiple times, but the same thing happens every time ... wheter i check "remember me" or not ... 

(as soon as i get Warhammer 40k Dawn Of War: Soulstorm to work fine in Wine i´ll be ditching Win, so i really need to this to work ;))

---

### Post by Joeb454 on 2008-05-20
Personally, I'd stick with Firefox 3. I've found it to be more efficient than FF2 (I've found memory leaks are gone). Also support for FF2 will be dropped by Mozilla at the end of this year, so FF3 is the wise choice :)

---

### Post by kestrel1 on 2008-05-20
I would be inclined to disagree, respectfully. FF3 does not work too well at present, that is the reason for installing FF2.

---

### Post by Joeb454 on 2008-05-20
Like I said, it depends on the OP's experience with Firefox 3. Personally, I have found it to be far better than FF2, though I can understand others installing the older version :)

---

### Post by kestrel1 on 2008-05-20
I do like some of the new features of FF3, but had so much trouble with it I had to do something else. When the full release comes out I may try it again then.

---

### Post by PmDematagoda on 2008-05-20
This thread mostly concerns a (possible) technical problem with the forums, therefore it has been moved to the Forum Feedback and Help section.

---

### Post by Joeb454 on 2008-05-20
Sounds fair enough :) I can't figure out why the OP is experiencing this though. Having said that, I haven't actually logged into the forums for months (I have "remember me" enabled :p)

---

### Post by Sef on 2008-05-20
> Personally, I'd stick with Firefox 3. I've found it to be more efficient than FF2 (I've found memory leaks are gone). Also support for FF2 will be dropped by Mozilla at the end of this year, so FF3 is the wise choice

Don't drop FF3, it has gone to RC1 now, so it should be updated to that soon by Ubuntu.  In June is should go to stable, so all these problems should be worked out by then.

I would simply download another browser for now, if you are that unhappy with firefox3 beta.  Just go into Applications > Add/Remove > search: browser > and select what you want.  I would chose either Seamonkey, which FF is based on or Epiphany.  Try them both out, if you are not sure which one to select.

---

### Post by Fizz_sweden on 2008-05-20
> **ad_267 said:**
> Hmm I just logged out and the Captcha image works for me on Firefox 3. I also have no problem logging in. I'm not sure why you'd be having these problems. Do you have cookies enabled?

are they enabled by default? (wish i could check for myself, but since starting up ubuntu and then restarting windows is a bit tedious, hope you understand)


i like FF3, so i think ill stick to that for now ... the only thing so far that´s not suport FF3 is my bank, and i can use my GF´s computer for that (she´s not fully convinced about ubuntu yet) ..

---

### Post by Myglaren on 2008-05-20
> **Fizz_sweden said:**
> are they enabled by default? (wish i could check for myself, but since starting up ubuntu and then restarting windows is a bit tedious, hope you understand)


i like FF3, so i think ill stick to that for now ... the only thing so far that´s not suport FF3 is my bank, and i can use my GF´s computer for that (she´s not fully convinced about ubuntu yet) ..

I'm using Ff3 (B3r5 here, RC1 on the (Vista) Laptop)
No problems other than just in the past few minutes posting has become a slight problem in that it will only accept the 'quote' option.
I have given this site full permissions with "NoScript" but it is still blocking some options.

---

### Post by Fizz_sweden on 2008-05-20
well ... i havent found any solution yet ... =/

if anyone has any ideas im more than glad to try them out! .. :)

---

### Post by kestrel1 on 2008-05-20
Not sure if this has anything to do with it, but have you got Flash & Java installed?
To check this type:
```
about:plugins
```
in to the address bar of FF3.

---

### Post by Fizz_sweden on 2008-05-21
flash is installed, not sure about java ... couldnt find it, but i were in a rush .... will check again ... :)

---

### Post by PriceChild on 2008-05-21
When we were in testing, preparing for the upgrade things like this were tested.

I personally tested recaptcha, both image and sound on firefox 3 on a vanilla ubuntu hardy and they worked fine. I assume that you've broken something if it doesn't work. More details about what doesn't work, or screenshots etc. would be helpful.

---

### Post by sports fan Matt on 2008-05-21
When I updated, it said the "ubuntu forums" menu wasnt compatible and im wondering what major changes were made that its not working in the Menu?

---

### Post by Fizz_sweden on 2008-05-22
well ... i installed ubuntu on my GF's computer yesterday, from the same CD, and it works fine on hers .. (writing this on FF3)

---

### Post by PriceChild on 2008-05-22
> **PriceChild said:**
> When we were in testing, preparing for the upgrade things like this were tested.

I personally tested recaptcha, both image and sound on firefox 3 on a vanilla ubuntu hardy and they worked fine. I assume that you've broken something if it doesn't work. More details about what doesn't work, or screenshots etc. would be helpful.

> **Fizz_sweden said:**
> well ... i installed ubuntu on my GF's computer yesterday, from the same CD, and it works fine on hers .. (writing this on FF3)I think that settles it then :P Find out what you broke :)

---

### Post by Fizz_sweden on 2008-05-22
haha .. i've only used it for a week or two .. cant see how i could have broken something already .... :)

the reCAPCHA part of the registration just showed an error msg when i tried to register, i can try to get a screenshot of that ... other than that theres nothing to show ... the forum webpage says nothing when i try to login ...

---

### Post by Fizz_sweden on 2008-05-22
here's a screenshot of the register error ...
doesnt say very much ... :-k

---

### Post by ad_267 on 2008-05-25
try going to [http://ubuntuforums.com/register.php?do=register](http://ubuntuforums.com/register.php?do=register) instead of [http://ph.ubuntuforums.com/register.php?do=register](http://ph.ubuntuforums.com/register.php?do=register)

---

### Post by kevdog on 2008-05-25
Not to beat a dead horse but there are problems (well documented) in fact with FF3, sqllite, and the linux kernel.  I'm certain this is probably not what the OP was refering too, however all is certainly not well with FF3 and linux in general.  There is no foreseeable fix on the horizon, possibly the next minor release if any.  When the Mozilla project balks and passes the problem down to the individual distro's to fix, you know there is a problem!

---

### Post by Fizz_sweden on 2008-05-26
> **ad_267 said:**
> try going to [http://ubuntuforums.com/register.php?do=register](http://ubuntuforums.com/register.php?do=register) instead of [http://ph.ubuntuforums.com/register.php?do=register](http://ph.ubuntuforums.com/register.php?do=register)

i registered on WIndows .... ;) ... i just want to login with Ubuntu/FF3 ... :)

anyone with any ideas on where to look? ... checked "about:plugins" and it looks the same on both computers (mine and my GF´s), and there was nothing about java on any of them ...

---

### Post by PriceChild on 2008-05-27
> **kevdog said:**
> Not to beat a dead horse but there are problems (well documented) in fact with FF3, sqllite, and the linux kernel.  I'm certain this is probably not what the OP was refering too, however all is certainly not well with FF3 and linux in general.  There is no foreseeable fix on the horizon, possibly the next minor release if any.  When the Mozilla project balks and passes the problem down to the individual distro's to fix, you know there is a problem!Last I heard, they were patching firefox for this, as they wanted to support linux as is, rather than how it 'should' be.

---

### Post by Jerry41 on 2008-06-06
I logged on and posted yesterday from UBUNTU 8.04/Firefox 3b5. Everything worked fine. This morning I tried to log on, but cannot even put a cursor on the username field. I had to log on from XP/Firefox2 to get here.
Interesting.
I think Ill have some squid sushi and wait with baited breath for developments.
:popcorn:

---

### Post by Fizz_sweden on 2008-06-09
> **Jerry41 said:**
> I logged on and posted yesterday from UBUNTU 8.04/Firefox 3b5. Everything worked fine. This morning I tried to log on, but cannot even put a cursor on the username field. I had to log on from XP/Firefox2 to get here.
Interesting.
I think Ill have some squid sushi and wait with baited breath for developments.
:popcorn:

i'm not as lonely anymore, i guess .... :)

well, well ... untill DoW: Soulstorm works flawlessly on ubuntu i will keep my win partion anyway ...

---

### Post by Jerry41 on 2008-06-10
By George, I think I've got it!   :cool:

I had zoomed in on text earlier & I believe that must have thrown the field out of kilter. I clicked on "View  Zoom  Reset" and it solved my login problem.

---

