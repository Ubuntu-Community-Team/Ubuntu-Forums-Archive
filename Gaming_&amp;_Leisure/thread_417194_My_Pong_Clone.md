---
title: "My Pong Clone"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by trager on 2007-04-21
I worte a pong clone a while ago and it can be downloaded from:

[http://www.darkdawn.co.uk/files/Pong.tar.gz](http://www.darkdawn.co.uk/files/Pong.tar.gz)

Check out the Pong page at [http://www.darkdawn.co.uk/](http://www.darkdawn.co.uk/) for further information such as dependancies.

Unless you are a Pong fan you probably shouldn't tell me what you think :P.

Have Fun

Paul

---

### Post by hikaricore on 2007-04-22
Looks very nice from the screens, I'll check it out later today. :)

edit: Tried to run a quick make on it and got:

> 
ssprite.h: In member function ‘void stDB_Window::Delete_Control(int)’:
sprite.h:432: warning: suggest parentheses around assignment used as truth value
make: *** [all] Error 1


>.< on both Edgy and Feisty.

---

### Post by trager on 2007-04-22
Your compiler stopped on a warning?

Much strangeness I'll have a look.

---

### Post by lakersforce on 2007-04-22
I installed all the required libraries, unpacked the file and ran a "make" in the Pong folder.

And unfortunately I got a whole lot of errors, to many to print here. Actually I got so many that they would not fit in my terminal window. But many of them are similar in their structure, so I will print (a random) one:

```
sprite.h:1281: fejl: &#8216;GL_TEXTURE_WRAP_S&#8217; was not declared in this scope
```

---

### Post by trager on 2007-04-22
Despite being 2D the game requires OpenGL to run.  
It looks, to me (<- Linux Noob), like you don't have a OpenGL driver installed for your video card.  If there isn't one available perhaps there is a software driver.

---

### Post by lakersforce on 2007-04-22
I might have made a mistake somewhere, but it is not because of lack of OpenGL system support (all OpenGL games works).

I downloaded your file, unpacked it (using the Gnome graphic file-unpacker), installed the libraries you state is required on your website and went to my Pong folder and typed in "make".

Let me print another (random) line:

```
pong1.cpp:793: fejl: &#8216;score_sound&#8217; was not declared in this scope
```

The process stopped with:

```
make: *** [all] Fejl 1
```

---

### Post by trager on 2007-04-22
I'll have a look lakersforce but there certainly seems to be some kind of compilation error for you.  

What are you using to compile btw , I am using g++ 4.0, gcc -4.0 and gcc with no problems other than the warning report by hikaricore.

BTW that is just a warning Hikaricore ./Pong and it should run, provided you have a sound card :/.

..should of made a binary.

---

### Post by hikaricore on 2007-04-22
make errors != binary

lol

> [hikaricore@devistate:/media/devistate/Pong]$ gcc --version
gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

Maybe I should try compiling it on a dapper live cd. heh  *shrug*

---

### Post by lakersforce on 2007-04-22
```
rune@rune-desktop:~$ gcc --version
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
```

---

### Post by trager on 2007-04-22
Your compiler option to treat warnings as errors doesn't give my poor coding skills a chance :P

Funny you should mention the dapper live CD, thats exactly what I installed from and it's at least 9 months old too, hence:

paul@paul-desktop:~$ gcc --version
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

---

### Post by hikaricore on 2007-04-22
I even tried:

make -i

but no luck, I'll boot up another system with a live cd, install the required libs to ram and see if I can complie.

---

### Post by trager on 2007-04-22
Thanks for the persistance Hikaricore, especially for a simple pong clone.  Would be nice to know if anyone other than me has managed to this working.

If you managed to get it to work from a live cd I'd imagine it'd be very slow unless you could get your gfx cards opengl driver working.  ...

I've just republished the code to [http://www.darkdawn.co.uk/files/Pong.tar.gz](http://www.darkdawn.co.uk/files/Pong.tar.gz), this version has the references to the windows and control objects removed as they arent actually required.

This version also contains a binary which may or may not work.

---

### Post by rolando2424 on 2007-04-22
> **trager said:**
> Thanks for the persistance Hikaricore, especially for a simple pong clone.  Would be nice to know if anyone other than me has managed to this working.

If you managed to get it to work from a live cd I'd imagine it'd be very slow unless you could get your gfx cards opengl driver working.  ...

I've just republished the code to [http://www.darkdawn.co.uk/files/Pong.tar.gz](http://www.darkdawn.co.uk/files/Pong.tar.gz), this version has the references to the windows and control objects removed as they arent actually required.

This version also contains a binary which may or may not work.

Well, I only saw the thread now :D

The Binary WORKS! (or at least worked for me... Ubuntu Edgy Eft).

The game is nice, even though I beat the Easy difficult on my first try, and the Hard difficult on my second try (I got distracted and lost 3-5 on the first, but then I've won 5-2 on the second).

However the Twister mode made me feel a little dizzy... It certantly has a "twist" ( :lolflag: ), but perhaps you should put a warning before the game starts...

Now back to the Twister.

Perhaps you should make the Hard difficulty "harder".

And there is only one problem with the Twister, is that when the screen is twisting, the corners can disappear when the image is at 90º and 270º and you can't see your're player... But I guess that's part of the difficulty.

---

### Post by lakersforce on 2007-04-22
I still get errors when compiling, but the binary works. Very nice, nice particle effects :)

---

### Post by trager on 2007-04-22
Cool.  It lives. 

Really would like to know why it isn't compiling for you guys.

Thanks for the input guys.

---

### Post by Landser on 2007-04-22
> **trager said:**
> Cool.  It lives. 

Really would like to know why it isn't compiling for you guys.

Thanks for the input guys.

First of all, you need the following dev packages:
libsdl1.2-dev, libsdl-image1.2-dev, libsdl-mixer1.2-dev, libsdl-ttf2.0-dev

You also have a code error on line 237, sprite.h:

```
	stDB_Sprite::stDB_Sprite(float px, float py, float pz, cls_Animation *_ani);
```

Needs to be changed to:

```
stDB_Sprite(float px, float py, float pz, cls_Animation *_ani);
```

And it compiles now!

---

### Post by trager on 2007-04-22
That overloaded constructor for the sprite class was never implemented on this project but yeah it is rubbish.
You guys are using g++, right?

I mean why compile for me but noone else?

---

### Post by hikaricore on 2007-04-22
> **trager said:**
> That overloaded constructor for the sprite class was never implemented on this project but yeah it is rubbish.
You guys are using g++, right?

I mean why compile for me but noone else?

I think it's honestly just the different versions of gcc.

Yours is like: "eh ok bad line oh well life goes on"

Ours is like: "ZOMG Wtf lazerzpewpew!!!  Someone set up us t3h make!  All your errors are belong to us!"

Then they stab poor pong with a spork :/  truely a misguided childhood for our compiler.

Anyway.... checking out that binary :)  I just love games so I can pass up even pong once hehe.

---

### Post by hikaricore on 2007-04-22
> **Landser said:**
> First of all, you need the following dev packages:
libsdl1.2-dev, libsdl-image1.2-dev, libsdl-mixer1.2-dev, libsdl-ttf2.0-dev

You also have a code error on line 237, sprite.h:

```
	stDB_Sprite::stDB_Sprite(float px, float py, float pz, cls_Animation *_ani);
```

Needs to be changed to:

```
stDB_Sprite(float px, float py, float pz, cls_Animation *_ani);
```

And it compiles now!

Aye this worked fore me as well.  I like what I see so far.  :)

---

### Post by trager on 2007-04-23
And here we see the down side to copy-and-paste coding...

Well at least I know why it doesn't compile for you guys now, I'll clean up the offending line and republish tonight. 

Does anyone know if this is the kind of thing Ubuntu would put in their universe?

---

