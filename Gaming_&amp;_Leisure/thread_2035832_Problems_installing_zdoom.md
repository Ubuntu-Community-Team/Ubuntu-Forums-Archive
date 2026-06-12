---
title: "Problems installing zdoom"
date: 2012-07-31
forum: Gaming &amp; Leisure
---

### Post by Uvunter on 2012-07-31
Hello.

I want to install ZDoom and GZDoom. I followed this steps: [http://linuxinnovations.blogspot.com.es/2009/08/compile-zdoom-and-gzdoom-in-ubuntu.html]("http://linuxinnovations.blogspot.com.es/2009/08/compile-zdoom-and-gzdoom-in-ubuntu.html")

When running the make command, this appears:

```
[ 85%] Building CXX object src/CMakeFiles/zdoom.dir/sfmt/SFMT.o
[ 85%] Building CXX object src/CMakeFiles/zdoom.dir/sound/fmodsound.o
/home/ignacio/zdoom/trunk/src/sound/fmodsound.cpp:201:19: error: ‘FMOD_SPEAKERMODE_PROLOGIC’ no se declaró en este ámbito
make[2]: *** [src/CMakeFiles/zdoom.dir/sound/fmodsound.o] Error 1
make[1]: *** [src/CMakeFiles/zdoom.dir/all] Error 2
make: *** [all] Error 2
```

I've installed all dependences and fmod ( [http://zdoom.org/wiki/Compile_ZDoom_on_Linux#Get_the_FMOD_package]("http://zdoom.org/wiki/Compile_ZDoom_on_Linux#Get_the_FMOD_package") ). I'm running Ubuntu 12.04.

---

### Post by kd5mkv on 2012-07-31
I was unsuccessful also, the final step it doesn't execute. I have this:
Cannot find a game IWAD (doom.wad, doom2.wad, heretic.wad, etc.).
Did you install ZDoom properly? You can do either of the following:

1. Place one or more of these wads in the same directory as ZDoom.
2. Edit your zdoom-username.ini and add the directories of your iwads
to the list beneath [IWADSearch.Directories]

Looks like cool game.

---

### Post by Uvunter on 2012-07-31
> **kd5mkv said:**
> I was unsuccessful also, the final step it doesn't execute. I have this:
Cannot find a game IWAD (doom.wad, doom2.wad, heretic.wad, etc.).
Did you install ZDoom properly? You can do either of the following:

1. Place one or more of these wads in the same directory as ZDoom.
2. Edit your zdoom-username.ini and add the directories of your iwads
to the list beneath [IWADSearch.Directories]

Looks like cool game.

I can't do that because it's not installed due to my make error :(

But, in your case, it is very simple: just download doom.wad or doom2.wad, and put it in the correct folder, and then execute zdoom.

---

### Post by kd5mkv on 2012-07-31
I only install the depenencies and steps, maybe your missing a lib.
I have tried install twice installing zdoom. So if take a iwad and place it in same folder it will execute like the wiki states. Lets see. thx

---

### Post by kd5mkv on 2012-07-31
POW that ./zdoom work like a charm after:
mv doom1.wad ~/trunk/release. I move the folder and it opened. great!

---

