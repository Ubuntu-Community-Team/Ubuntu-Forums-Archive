---
title: "Python Angry Tux"
date: 2011-02-21
forum: Gaming &amp; Leisure
---

### Post by lkjoel on 2011-02-21
This is the discussion thread for Python Angry Tux

[COLOR="Red"]PLEASE READ:[/COLOR]
We need volunteers to manage new users.
I have to devote more time to my studies, so I will probably not be available to manage new users/add code/do everything else.
If you are interested in managing new users, please PM me as soon as possible.

HOWTOS:

[LIST]
[*]How to join:
Get a sourceforge.net account.
Then go here:
[http://angrytux.sourceforge.net/develop.html]("http://angrytux.sourceforge.net/develop.html")
Fill in the form
Click on Submit.
Then follow the instructions.
Make sure that you copy EXACTLY the text on the Contents.
We will try to add you to the project as soon as possible.
While you are waiting for us to add you, please vote on these polls:
[http://poll.fm/2r13w]("http://poll.fm/2r13w")
[http://poll.fm/2sem8]("http://poll.fm/2sem8")
[*]SVN
Preparation and Downloading:
```
sudo apt-get install svn
svn co https://angrytux.svn.sourceforge.net/svnroot/angrytux angrytux
cd angrytux

```
To fetch changes:
```
svn up

```
To add changed files:
[LIST]
[*]Method 1:
```
svn add *file*
svn commit

```
[*]Method 2:
```
./svnradd.sh .
./svncommit.sh

```
[/LIST]

[*]GIT
First set up:

[LIST]
[*] [http://help.github.com/git-installation-redirect]("http://help.github.com/git-installation-redirect")
[*] [http://help.github.com/linux-key-setup/]("http://help.github.com/linux-key-setup/")
[/LIST]

Then:
```
USERNAME=yoursourceforgeusername
```
```
git clone ssh://$USERNAME@angrytux.git.sourceforge.net/gitroot/angrytux/angrytux 
cd angrytux

```
To fetch changes:
```
git pull
git update

```
To add changed files:
[LIST]
[*]Method 1:
```
git add *file*
git commit
git push

```
[*]Method 2:
```
./gitradd.sh .
./gitcommit.sh

```
[/LIST]
[*]Mercurial
First set up:
[https://help.ubuntu.com/community/Mercurial]("https://help.ubuntu.com/community/Mercurial")

Then:
```
USERNAME=yoursourceforgeusername
```
```
hg clone ssh://$USERNAME@angrytux.hg.sourceforge.net/hgroot/angrytux/angrytux
cd angrytux

```
To fetch changes:
```
hg pull
hg update

```
To add changed files:
[LIST]
[*]Method 1:
```
hg add *file*
hg commit
hg push

```
[*]Method 2:
```
./hgradd.sh .
./hgcommit.sh

```
[/LIST]
[/LIST]

---

### Post by DrAcid on 2011-02-22
**lkjoel**
Good Job! :)

I've been thinking: since there are some people *already* working on the Angry Tux game, shouldn't we try and contact them and... well, join them?
There's no point starting a whole new project when there already IS one. Why not join forces?
Strength lies in unity, after all! ;)

---

### Post by lkjoel on 2011-02-22
> **DrAcid said:**
> **lkjoel**
Good Job! :)

I've been thinking: since there are some people *already* working on the Angry Tux game, shouldn't we try and contact them and... well, join them?
There's no point starting a whole new project when there already IS one. Why not join forces?
Strength lies in unity, after all! ;)
I don't know.
They are using C++ (Entirely different from python), and we are using Python.
There was a fork somewhere in Angry Tux, which then we took two different languages.
I have (currently) no knowledge of C++, except the syntax.
Maybe the C++ guys could make some libraries for the game, but I think they have already started making the game.
I think that for now, we should just continue, and see whats going to happen.
What do you think?

---

### Post by icodemonkey on 2011-02-23
look at how many <insert app/game of choice> there is for Linux, we're just adding to the diversity. 
i know i bit about python but i do run a web dev business so project admin is something i do a lot of.

---

### Post by ubudog on 2011-02-23
Great job with the thread, lkjoel.
If you need ANY Python help, let me know.  While I'm still learning, I may be useful.  :-)

---

### Post by lkjoel on 2011-02-23
> **ubudog said:**
> Great job with the thread, lkjoel.
If you need ANY Python help, let me know.  While I'm still learning, I may be useful.  :-)
Thanks!

---

### Post by icodemonkey on 2011-02-23
> **ubudog said:**
> Great job with the thread, lkjoel.
If you need ANY Python help, let me know.  While I'm still learning, I may be useful.  :-)

we have a github project @ [https://github.com/icodemonkey/Angry_Tux](https://github.com/icodemonkey/Angry_Tux)
and a sourceforge page @ [https://sourceforge.net/projects/angrytux/](https://sourceforge.net/projects/angrytux/)

feel free to join or just lurk

---

### Post by lkjoel on 2011-02-23
I just can't understand how to use Git.
Can anyone help me?
**== EDIT ==**
Nevermind, I finally got it.
It's quite simple, and very similar to SVN.

---

### Post by lkjoel on 2011-02-23
Is the README ok?

---

### Post by icodemonkey on 2011-02-24
> **lkjoel said:**
> Is the README ok?

epic readme is epic had no probs with it on any os/platform

---

### Post by DrAcid on 2011-02-24
Cool readme! although You have to install additional python-imaging library... ImageTK won't work without it...
what are the plans, dear sirs?

I say we create game mechanics fist and menu later. right?
That diagram in previous thread was a good beginning! We should use it!

---

### Post by lkjoel on 2011-02-24
> **DrAcid said:**
> Cool readme! although You have to install additional python-imaging library... ImageTK won't work without it...
...
I updated the README

---

### Post by livelite on 2011-02-24
Awesome, I'll try it out.

**::: edit :::**

Got it running, but needed:

```
sudo apt-get install python-imaging-tk
```

Add **python-imaging-tk** to the readme.

Start screen looks nice! But we probably don't need that second start button on the bottom.

---

### Post by lkjoel on 2011-02-24
> **livelite said:**
> Awesome, I'll try it out.

**::: edit :::**

Got it running, but needed:

```
sudo apt-get install python-imaging-tk
```

Add **python-imaging-tk** to the readme.

Start screen looks nice! But we probably don't need that second start button on the bottom.
Thanks for the info.
I will update it.
I don't exactly know if it would be good to remove the second start button, since I think non-geeks would rather want a simple button.
We'll see.

---

### Post by DrAcid on 2011-02-24
Guys, I'm can log into Sourceforge via my Lauchpad OpenID...
How do I commit changes? it asks me for login/password. Of what?
Please help. :P

I've an updated screen.

---

### Post by Kirboosy on 2011-02-24
Alright I'm jumping on board :D

---

### Post by livelite on 2011-02-24
I want to join the developers on GitHub. I didn't see how to send a request there.
But I'm successfully handling Git, the instructions made it very easy. Thanks!

---

### Post by lkjoel on 2011-02-24
> **DrAcid said:**
> Guys, I'm can log into Sourceforge via my Lauchpad OpenID...
How do I commit changes? it asks me for login/password. Of what?
Please help. :P

I've an updated screen.
You should register for a full user account, and not with an OpenID.
It will let you do much more, trust me.
PM me your sourceforge username, and I will add you to the project.
I cannot add you to the GitHub project though, since I am not an admin.
Ask icodemonkey for Git.

---

### Post by lkjoel on 2011-02-24
> **livelite said:**
> I want to join the developers on GitHub. I didn't see how to send a request there.
But I'm successfully handling Git, the instructions made it very easy. Thanks!
First get a GitHub account.
Then give icodemonkey your username for Git, and he should add you to the project.
If you want to join SVN, get a sourceforge.net account, and PM me your username so that I can add you.

---

### Post by Kirboosy on 2011-02-24
Sent a request for developer status on SourceForge. :)

---

### Post by lkjoel on 2011-02-24
> **Caboose885 said:**
> Sent a request for developer status on SourceForge. :)
You are now an official developer ;-)

---

### Post by lkjoel on 2011-02-24
Something really weird is happening.
First, I try to add files to SVN, but then it says that .SVN is not working.
Then I try to re-checkout the repository, and after many tries, I finally got to do it.
Then I try to run "svn up", and it tries to delete the data directory.
That's ok, since I have a backup copy.
So then I try to re-add the data directory with this error message:
```
./svncommit.sh
Adding         data
svn: Commit failed (details follow):
svn: Server sent unexpected return value (405 Method Not Allowed) in response to MKCOL request for '/svnroot/angrytux/!svn/wrk/f207b0d0-fade-4d16-a03c-e0fe90541b67/data'
svn: Your commit message was left in a temporary file:
svn:    'Angry_Tux/svn-commit.3.tmp'

```
Can anyone help me?
Thanks!
**== EDIT ==**
SVN is screwed up.
The data directory is not even coming up with "svn co -r 6 ..."
**== EDIT 2 ==**
I fixed it.
This is what I did:
I went into the buggy directory.
Then I checked out the repository again.
I copied and pasted all of the files in the new directory just checked out, into the parent directory.
Then I ran "svn up"

---

### Post by icodemonkey on 2011-02-24
To all following this thred: on the 4/3/11 the github project will close as having a SF project and a Github just seemed unnecessary, if you want to join (or rejoin) PM ether Myself or lkjoel with your sourceforge U/N and you will be added.

---

### Post by lkjoel on 2011-02-24
> **icodemonkey said:**
> To all following this thred: on the 4/3/11 the github project will close as having a SF project and a Github just seemed unnecessary, if you want to join (or rejoin) PM ether Myself or lkjoel with your sourceforge U/N and you will be added.
I am making a mailing list so that it would be simpler.
They send it to the mailing list, and one (or both) or us adds them to the project.

---

### Post by Kirboosy on 2011-02-24
Are we going to communicate via UF or IRC or Email? How we doing this?

---

### Post by lkjoel on 2011-02-24
> **Caboose885 said:**
> Are we going to communicate via UF or IRC or Email? How we doing this?
I don't know.
Maybe wedoist (I used it for other projects, and it works quite well).
Could you PM me your e-mail address?
That is the only way for me to add you to wedoist.

---

### Post by Kirboosy on 2011-02-25
So I have a friend who is an awesome modeler/drawer. She said she will draw up any images we need. She has already started sketching things. She is really stoked about it. :D Oh and she will most likely join "developer" status her name will probably be like "3DElizabeth" or something like that. 

Just giving you a heads up :)

---

### Post by lkjoel on 2011-02-25
> **Caboose885 said:**
> So I have a friend who is an awesome modeler/drawer. She said she will draw up any images we need. She has already started sketching things. She is really stoked about it. :D Oh and she will most likely join "developer" status her name will probably be like "3DElizabeth" or something like that. 

Just giving you a heads up :)
Great!
That's what we really needed!
I think we need Angry Tux facing to the right, a sling (maybe made with snow and ice) and a backdrop for now.
Oh and somehow I cannot add Ubudog (who has requested to join).
I get this error message:

[INDENT]The user you have attempted to add to this project is not active. Only active users can be added. Please wait until this user is active to add them to your project.[/INDENT]

---

### Post by jakejw93 on 2011-02-25
So what stage is this project at now?

---

### Post by Kirboosy on 2011-02-25
> **lkjoel said:**
> [INDENT]The user you have attempted to add to this project is not active. Only active users can be added. Please wait until this user is active to add them to your project.[/INDENT]

I'm guessing he hasn't activated his account through the conformation email yet. IDK :(

> So what stage is this project at now?

We are just starting. We are really in the brainstorming/planning stage. We have an awesome README.txt though! ;)

---

### Post by livelite on 2011-02-25
> **lkjoel said:**
> Great!
That's what we really needed!
I think we need Angry Tux facing to the right, a sling (maybe made with snow and ice) and a backdrop for now.
Oh and somehow I cannot add Ubudog (who has requested to join).
I get this error message:

[INDENT]The user you have attempted to add to this project is not active. Only active users can be added. Please wait until this user is active to add them to your project.[/INDENT]

And Tux needs to be round, or close to round, so he can roll like a ball when he hits the ground.

As for sourceforge, I'm not able to activate my account either, because the activation email has never arrived.  I contacted them and hopefully they'll sort it out.

---

### Post by lkjoel on 2011-02-25
> **livelite said:**
> And Tux needs to be round, or close to round, so he can roll like a ball when he hits the ground.

As for sourceforge, I'm not able to activate my account either, because the activation email has never arrived.  I contacted them and hopefully they'll sort it out.
Sorry!
I think I forgot to add you!
Could you re-pm me your e-mail address?
I'm really sorry for that. :(
**=== EDIT ===**
I tried to add you, but it somehow didn't let me.
It said that you were not active.
**=== EDIT 2 ===**
You are added.

---

### Post by lkjoel on 2011-02-26
> **livelite said:**
> And Tux needs to be round, or close to round, so he can roll like a ball when he hits the ground.

As for sourceforge, I'm not able to activate my account either, because the activation email has never arrived.  I contacted them and hopefully they'll sort it out.
Try making a new user account, such as livelite1.
Make sure that you entered your e-mail correctly on the sign up.
Some users had to do that.

---

### Post by DrAcid on 2011-03-04
Guys, any news?
What's the progress? Artwork? engine?

I'm trying to learn some python to help... :P

---

### Post by livelite on 2011-03-04
> **DrAcid said:**
> Guys, any news?
What's the progress? Artwork? engine?

I'm trying to learn some python to help... :P

I am experimenting with pybox2d (+pygame), to base our engine on.  I will share later in the repository what I did.

---

### Post by juancarlospaco on 2011-03-04
> **livelite said:**
> I am experimenting with pybox2d (+pygame), to base our engine on.  I will share later in the repository what I did.

[http://www.pilas-engine.com.ar/](http://www.pilas-engine.com.ar/)

**See the Video !**
(it already has a working user-controled Tux actor)

---

### Post by lkjoel on 2011-03-04
> **juancarlospaco said:**
> [http://www.pilas-engine.com.ar/](http://www.pilas-engine.com.ar/)

**See the Video !**
(it already has a working user-controled Tux actor)
Thanks for the link!
Finally there is a simple game engine!

---

### Post by juancarlospaco on 2011-03-04
> **lkjoel said:**
> Thanks for the link!
Finally there is a simple game engine!

If you really consider that engine tell me if you need help to traduce docs or something.

---

### Post by lkjoel on 2011-03-05
> **juancarlospaco said:**
> If you really consider that engine tell me if you need help to traduce docs or something.
Yo sé un poco de español (was that correct?:p)

---

### Post by livelite on 2011-03-05
> **livelite said:**
> I am experimenting with pybox2d (+pygame), to base our engine on.  I will share later in the repository what I did.

Hey, I commited the code to the sourceforge svn repository.  Check it out.  The game already has towers with bears (circles), and you can sling a tux (circle) at them to show them what happens when they steal Tux's fishes :) (possibility for the story line)


You'll need to get and install [pybox2d (code.google.com/p/pybox2d/)]("http://code.google.com/p/pybox2d/").

Download the source and follow the instructions that comes in the INSTALL file.

Update the repository

```
svn up
```

Then run

```
python angrytux_b2.py
```

:popcorn:

---

### Post by lkjoel on 2011-03-06
> **livelite said:**
> Hey, I commited the code to the sourceforge svn repository.  Check it out.  The game already has towers with bears (circles), and you can sling a tux (circle) at them to show them what happens when they steal Tux's fishes :) (possibility for the story line)


You'll need to get and install [pybox2d (code.google.com/p/pybox2d/)]("http://code.google.com/p/pybox2d/").

Download the source and follow the instructions that comes in the INSTALL file.

Update the repository

```
svn up
```

Then run

```
python angrytux_b2.py
```

:popcorn:
I get an error message:
```
user@computer:~/Angry_Tux/$ python angrytux_b2.py
Traceback (most recent call last):
  File "angrytux_b2.py", line 7, in <module>
    from b2_framework import *
  File "/home/user/Angry_Tux/b2_framework.py", line 26, in <module>
    from b2_settings import fwSettings
ImportError: No module named b2_settings

```
I installed the libraries from the Ubuntu repositories, from the link you gave us (2.1.0) and from pip.
I have build-essential, python-dev, swig and python-pygame

---

### Post by livelite on 2011-03-06
> **lkjoel said:**
> I get an error message:
```
user@computer:~/Angry_Tux/$ python angrytux_b2.py
Traceback (most recent call last):
  File "angrytux_b2.py", line 7, in <module>
    from b2_framework import *
  File "/home/user/Angry_Tux/b2_framework.py", line 26, in <module>
    from b2_settings import fwSettings
ImportError: No module named b2_settings

```
I installed the libraries from the Ubuntu repositories, from the link you gave us (2.1.0) and from pip.
I have build-essential, python-dev, swig and python-pygame

Do you have the file b2_settings.py?  It should be there with b2_framework.py, pygame_framework.py, and angrytux_b2.py

---

### Post by lkjoel on 2011-03-06
> **livelite said:**
> Do you have the file b2_settings.py?  It should be there with b2_framework.py, pygame_framework.py, and angrytux_b2.py
It isn't there.
Could you please add it to the SVN?

I am currently making the new developer form.
I'll add it in a few hours (once it is finished).

---

### Post by lkjoel on 2011-03-06
I finished the new developer page.
How does everyone like it?
[http://angrytux.sourceforge.net/develop.html]("http://angrytux.sourceforge.net/develop.html")

---

### Post by ubudog on 2011-03-07
> **lkjoel said:**
> I finished the new developer page.
How does everyone like it?
[http://angrytux.sourceforge.net/develop.html]("http://angrytux.sourceforge.net/develop.html")

Very nice, I love it! :D:D

---

### Post by icodemonkey on 2011-03-07
<keanu_reeves> Whoa!! </keanu_reeves> i fall off the world for a few days and things blow up.
But i'm back now so <rubs hands together>???

---

### Post by livelite on 2011-03-07
> **lkjoel said:**
> It isn't there.
Could you please add it to the SVN?

I am currently making the new developer form.
I'll add it in a few hours (once it is finished).

It's in the svn repository, here's the direct link:

[http://angrytux.svn.sourceforge.net/viewvc/angrytux/b2_settings.py?revision=17&view=markup](http://angrytux.svn.sourceforge.net/viewvc/angrytux/b2_settings.py?revision=17&view=markup)

I only used svn, since I thought that's what we decided to go with.  Or will we be using git and mercurial as well?

Good job on the developer page, looks very neat!

---

### Post by livelite on 2011-03-07
> **juancarlospaco said:**
> If you really consider that engine tell me if you need help to traduce docs or something.

Yes, it would be so nice to have it available in english.

---

### Post by ubudog on 2011-03-08
I could help with translation of the game into other languages, if we need it.  

:-)

---

### Post by meborc on 2011-03-08
I will be glad to be a tester :D no real programming ability between my ears

at the moment, when running angrytux_b2 I get the following message:
```
$ python angrytux_b2.py 
Traceback (most recent call last):
  File "angrytux_b2.py", line 7, in <module>
    from b2_framework import *
  File "/home/kaspar/angrytux/b2_framework.py", line 53, in <module>
    class fwQueryCallback(b2QueryCallback):
NameError: name 'b2QueryCallback' is not defined

```

I also had to install python-box2d to get through another message

---

### Post by livelite on 2011-03-08
> **meborc said:**
> I will be glad to be a tester :D no real programming ability between my ears

at the moment, when running angrytux_b2 I get the following message:
```
$ python angrytux_b2.py 
Traceback (most recent call last):
  File "angrytux_b2.py", line 7, in <module>
    from b2_framework import *
  File "/home/kaspar/angrytux/b2_framework.py", line 53, in <module>
    class fwQueryCallback(b2QueryCallback):
NameError: name 'b2QueryCallback' is not defined

```

I also had to install python-box2d to get through another message

I installed pybox2d from the [http://code.google.com/p/pybox2d/](http://code.google.com/p/pybox2d/),  maybe there's a difference from the repository one. Although the versions seem to match up..

---

### Post by lkjoel on 2011-03-08
> **livelite said:**
> It's in the svn repository, here's the direct link:

[http://angrytux.svn.sourceforge.net/viewvc/angrytux/b2_settings.py?revision=17&view=markup](http://angrytux.svn.sourceforge.net/viewvc/angrytux/b2_settings.py?revision=17&view=markup)

I only used svn, since I thought that's what we decided to go with.  Or will we be using git and mercurial as well?

Good job on the developer page, looks very neat!
Sorry for the late reply!
I love the new engine.
I don't know exactly about git and mercurial.
Maybe a new poll for that?

---

### Post by lkjoel on 2011-03-08
> **livelite said:**
> I installed pybox2d from the [http://code.google.com/p/pybox2d/](http://code.google.com/p/pybox2d/),  maybe there's a difference from the repository one. Although the versions seem to match up..
You can also install box2d with a package manager (not apt, but python package manager)
```
sudo apt-get install python-pip
sudo pip install box2d --upgrade

```

---

### Post by lkjoel on 2011-03-08
New poll: Should we keep Git and Mercurial.
[http://poll.fm/2sem8]("http://poll.fm/2sem8")

---

### Post by livelite on 2011-03-09
> **lkjoel said:**
> New poll: Should we keep Git and Mercurial.
[http://poll.fm/2sem8]("http://poll.fm/2sem8")

How about we just use git?  I voted for just git in Other, but it just showed up as Other.

---

### Post by livelite on 2011-03-09
> **livelite said:**
> How about we just use git?  I voted for just git in Other, but it just showed up as Other.

Or how about Bazaar?  I just noticed it's available on sourceforge.
It's distributed, and easier to use, especially with Bazaar Explorer.

---

### Post by Kirboosy on 2011-03-10
I like bzr. On my last developer project we used bzr.

---

### Post by livelite on 2011-03-10
I use bzr for my own projects as well.
Initially I tried git, but bzr just seems easier to use. Plus when I heard Ubuntu uses bzr, I just went with it.

---

### Post by Kirboosy on 2011-03-10
Im thinking we need to make a level creator/editor. One up on angry birds. Also we should have an easy way to have community map packs added :D

---

### Post by livelite on 2011-03-10
> **Caboose885 said:**
> Im thinking we need to make a level creator/editor. One up on angry birds. Also we should have an easy way to have community map packs added :D

Certainly.  I can foresee this being one of the best features of the game.  Players will create all sorts of maps :D

For us developers it's time to get started proper - [*reading the manual*]("http://code.google.com/p/pybox2d/wiki/GettingStartedManual")

---

### Post by ubudog on 2011-03-10
> **Caboose885 said:**
> Im thinking we need to make a level creator/editor. One up on angry birds. Also we should have an easy way to have community map packs added :D

+1

This would definitely be an awesome feature to have.

---

### Post by ubudog on 2011-03-10
> **livelite said:**
> Certainly.  I can foresee this being one of the best features of the game.  Players will create all sorts of maps :D

For us developers it's time to get started proper - [*reading the manual*]("http://code.google.com/p/pybox2d/wiki/GettingStartedManual")

Thanks for that link!

Off to reading...

---

### Post by Kirboosy on 2011-03-10
> **livelite said:**
> Certainly.  I can foresee this being one of the best features of the game.  Players will create all sorts of maps :D

For us developers it's time to get started proper - [*reading the manual*]("http://code.google.com/p/pybox2d/wiki/GettingStartedManual")


Grabbing a pot of coffee and off I go to read! ;)

---

### Post by lkjoel on 2011-03-10
I'll add BZR and GIT as options to the poll, but somehow BZR doesn't work well on sourceforge.net.
Please re-vote on the poll (you might have to clear your cookies) since I have deleted some answers to keep the poll cleaner.

I'm really sorry about this, but I have to devote more time to studies. I'll be back on Easter.
If anyone could manage new users, that would be greatly appreciated.
Please PM me as soon as possible if you want to manage new users, and I'll add you on the list.

---

### Post by meborc on 2011-03-11
adding level creator will help grow the community around the game...

just look at xmoto and all the levels users have created :)

or look at the PS3 hit game LittleBigPlanet... over 3 million levels created :)

---

### Post by ubudog on 2011-03-11
> **meborc said:**
> adding level creator will help grow the community around the game...

just look at xmoto and all the levels users have created :)

or look at the PS3 hit game LittleBigPlanet... over 3 million levels created :)

Yep, LittleBigPlanet is a great example of that.  :-)

---

### Post by lkjoel on 2011-03-12
> **meborc said:**
> adding level creator will help grow the community around the game...
+1
I think that we should include an upload option on the level editor which will automatically upload the level to a separate SVN/GIT/HG/BZR repository.

---

### Post by livelite on 2011-03-12
> **lkjoel said:**
> +1
I think that we should include an upload option on the level editor which will automatically upload the level to a separate SVN/GIT/HG/BZR repository.

and in the game, we'll have the ability to download those levels

---

### Post by livelite on 2011-03-12
> **lkjoel said:**
> I'll add BZR and GIT as options to the poll, but somehow BZR doesn't work well on sourceforge.net.

Why is it that bzr doesn't work well on sourceforge?

---

### Post by Kirboosy on 2011-03-12
Because they chose not to support bzr? I guess they thought "we can't support every repository manager so we will select Git and SVN since they seem to be popular."

---

### Post by ubudog on 2011-03-12
What about a project icon for SF?  Ideas anyone?

---

### Post by lkjoel on 2011-03-13
BZR is supported, but it doesn't work well.
I think a good project icon would be a smaller version of Angry Tux.

And thanks to all of you who volunteered to help out with managing new users!
I greatly appreciate it.

---

### Post by ubudog on 2011-03-13
Yes, I agree, a smaller version of Angry Tux would be a nice icon.  :-)

---

### Post by livelite on 2011-03-13
> **lkjoel said:**
> BZR is supported, but it doesn't work well.

My question is why doesn't bzr work well on sf?

---

### Post by ubudog on 2011-03-15
Fellow developers, I am working on a new version of the web site for Angry Tux on my site.  Please let me know what you think.  This is still a work in progress...

[http://ubudog.homelinux.net/angrytux](http://ubudog.homelinux.net/angrytux)

---

### Post by livelite on 2011-03-15
> **ubudog said:**
> Fellow developers, I am working on a new version of the web site for Angry Tux on my site.  Please let me know what you think.  This is still a work in progress...

[http://ubudog.homelinux.net/angrytux](http://ubudog.homelinux.net/angrytux)

Nice.  Just correct the aspect ratio on that pic.
Perhaps we can have the developer form do a real submit, having email us the info.

---

### Post by ubudog on 2011-03-15
> **livelite said:**
> Nice.  Just correct the aspect ratio on that pic.

Yeah, it does look funky.  Brb.

---

### Post by ubudog on 2011-03-15
I think it looks a bit better now, you?

[http://ubudog.homelinux.net/angrytux](http://ubudog.homelinux.net/angrytux)

---

### Post by livelite on 2011-03-15
> **ubudog said:**
> I think it looks a bit better now, you?

[http://ubudog.homelinux.net/angrytux](http://ubudog.homelinux.net/angrytux)

The problem is width="200" height="200" in the img tag, which makes it a square.  Just scale down the image using gimp (keeping the ratio), put the smaller image in the img tag, and don't put any width and height.

---

### Post by ubudog on 2011-03-15
Cool, thanks, I'm gonna try that now.

---

### Post by ubudog on 2011-03-15
Like that, right?  Kinda fuzzy...

---

### Post by altonbr on 2011-03-23
Can we get this on github so I can collaborate easier?

---

### Post by ubudog on 2011-03-25
Devs - I have committed a Music directory along with a test song made with Hydrogen to the svn repo.  Let me know what you guys think.

---

### Post by ubudog on 2011-03-27
New svn changes...

Added support for playing .wav files into Angry Tux (for game music).

On clicking the play button, a simple little song starts.  

We are making good progress.  :guitar:

---

### Post by ubudog on 2011-03-28
> **vthiji10 said:**
> look at how many <insert app/game of choice> there is for Linux

Haha, yeah.

---

### Post by Kirboosy on 2011-03-28
Do we want .wav files for music? .Wav files are pretty chunky and large. I was thinking .ogg (since its open-source and smaller)

---

### Post by Vi3tHoneyX on 2011-03-28
This project sounds awesome!! I really hope you guys can get it working! ^_^

---

### Post by ubudog on 2011-03-28
> **Caboose885 said:**
> Do we want .wav files for music? .Wav files are pretty chunky and large. I was thinking .ogg (since its open-source and smaller)

Good idea.  .OGG would be better.  Anyone know if tkSnack supports .ogg's?

---

### Post by ubudog on 2011-03-28
> **Vi3tHoneyX said:**
> This project sounds awesome!! I really hope you guys can get it working! ^_^

Yep.  I think it will turn out great.  :D

---

### Post by Kirboosy on 2011-03-29
> **ubudog said:**
> Good idea.  .OGG would be better.  Anyone know if tkSnack supports .ogg's?


It says right [here]("http://packages.ubuntu.com/lucid/python-tksnack") that it does.

---

### Post by ubudog on 2011-03-29
Oh, cool.  I'll have to change the code around.  :-)

---

### Post by ubun2geek on 2011-10-06
Are you also on GOogle Code?
[http://code.google.com/p/angry-tux/](http://code.google.com/p/angry-tux/)

---

### Post by thatguruguy on 2011-10-07
> **ubun2geek said:**
> Are you also on GOogle Code?
[http://code.google.com/p/angry-tux/](http://code.google.com/p/angry-tux/)

As mentioned in the third post of this thread, that is a completely different project.

---

### Post by ubun2geek on 2011-10-07
> **thatguruguy said:**
> As mentioned in the third post of this thread, that is a completely different project.

Oops, guess I wasn't paying attention. How is the project going? All I see is a picture when it starts but nothing else.

---

