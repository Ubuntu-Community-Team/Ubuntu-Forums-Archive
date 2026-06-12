---
title: "Please help with Action Cube"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by ianb72 on 2007-05-06
I have just downloaded Action Cube after seein it on 
[How to download/install Action Cube]("http://66.249.91.104/translate_c?hl=en&u=http://www.ubuntugames.org/actioncube&prev=/search%3Fq%3DUbuntu%2Bgames%26hl%3Den%26sa%3DG")

But when I do the second step of the install

[HTML] sudo to tar - vxjpf ActionCube_v0.92.tar .bz2[/HTML]

I get this error

[HTML] sudo: to: command not found[/HTML]

Please help as this game reminds me of Counter strike I used to play on windoze but much much better.

Thanks
Ian

---

### Post by Perfect Storm on 2007-05-06
```
sudo jxfv ActionCube_v0.92.tar.bz2
```

---

### Post by ianb72 on 2007-05-06
> **Artificial Intelligence said:**
> ```
sudo jxfv ActionCube_v0.92.tar.bz2
```

tried that it said this:

[HTML] ian-m3gxx@ian-m3gxx-desktop:~/Desktop$ sudo jxfv ActionCube_v0.92.tar.bz2
Password:
sudo: jxfv: command not found
[/HTML]

:confused:

---

### Post by Perfect Storm on 2007-05-06
sorry it should have tar infront;

```
tar jxfv ActionCube_v0.92.tar.bz2
```


...time for me to get some sleep when I mess up the commands :-/

---

### Post by WinterWeaver on 2007-05-06
rofl AI

---

### Post by ianb72 on 2007-05-06
> **Artificial Intelligence said:**
> sorry it should have tar infront;

```
tar jxfv ActionCube_v0.92.tar.bz2
```


...time for me to get some sleep when I mess up the commands :-/

Cheers
That works great.

I've just watch the demo at

[Action cube Demo]("http://www.getdeb.net/app.php?name=ActionCube")

Man this is so much better than Counter strike and I had to buy half life first to play that!!!

Thanks

I'm off to play now!!! :) 

Ian

---

### Post by ianb72 on 2007-05-06
Well I would be if I could get it to run!!

What command do I use? As the 
[HTML]sh actioncube.sh[/HTML]

Doesn't work!!!

Ian

---

### Post by Perfect Storm on 2007-05-06
You need to be in that specific directory to do it.
```
cd <distination>
```

eg. cd myfolder

---

### Post by Perfect Storm on 2007-05-06
> **WinterWeaver said:**
> rofl AI

Stuff like that happens :) Been awake for 18 hours :popcorn:

---

### Post by ianb72 on 2007-05-06
> **Artificial Intelligence said:**
> You need to be in that specific directory to do it.
```
cd <distination>
```

eg. cd myfolder

Sorry it's late and I'm excited!!

Right I did that and got this!!!!!

[HTML]ian-m3gxx@ian-m3gxx-desktop:~/Desktop$ cd ActionCube
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/ActionCube$ sh actioncube.sh
.//bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/ActionCube$
[/HTML]:confused: :confused:

---

### Post by Perfect Storm on 2007-05-06
```
sudo aptitude install libsdl-image1.2
```

---

### Post by ianb72 on 2007-05-06
Done that now its coming up this

[HTML]ian-m3gxx@ian-m3gxx-desktop:~/Desktop/ActionCube$ sh actioncube.sh .//bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
ian-m3gxx@ian-m3gxx-desktop:~/Desktop/ActionCube$
[/HTML]

Should I do this?
[HTML]sudo aptitude install libsdl-mixer1.2[/HTML]

Ian

---

### Post by Perfect Storm on 2007-05-06
yep ^_^

---

### Post by ianb72 on 2007-05-06
How could I, or could I make a Launcher to the Actioncube.sh file?

It is located here [HTML]home/ian-m3gxx/Desktop/ActionCube[/HTML]

but when I make a Launcher with the command [HTML]home/ian-m3gxx/Desktop/ActionCube/sh actioncube.sh [/HTML]

It doesn't launch any ideas??

Ian

---

### Post by MonkeyBoy on 2007-05-06
You could go to getdeb.net and get hold of the debs for it which is the easy option.

[http://www.getdeb.net/category.php?id=1](http://www.getdeb.net/category.php?id=1)

---

### Post by Sockerdrickan on 2007-05-06
sh /home/ian-m3gxx/Desktop/ActionCube/actioncube.sh

---

### Post by ianb72 on 2007-05-06
I couldn't get that to work!!

Ian

---

### Post by RomeReactor on 2007-05-06
Hi. Try it like this:

```
sh -c "cd /home/ian-m3gxx/Desktop/ActionCube && ./actioncube.sh"
```

---

### Post by ianb72 on 2007-05-07
> **RomeReactor said:**
> Hi. Try it like this:

```
sh -c "cd /home/ian-m3gxx/Desktop/ActionCube && ./actioncube.sh"
```

Yeah that did the trick

Thanks very much

---

### Post by Sweet Spot on 2007-05-17
This thread has thoroughly confused me. I don't know if particular code is related to other code, or if there's just one definitive answer which helped the OP get it installed. I did post a new thread about this, but I figured that for the sake of other people, for future reference, I could just get a straight answer to this:

I downloaded the ActionCube_v0.92.tar.bz2 file, it's sitting on my desktop. 

Now let's say for all intents and purposes, that my user name is : puppy. How do I install this thing ? And please, step by step as if I'm totally inane. (which in this instance, I very well may be !)  I'd love a good copy paste method please. I usually copy everything like this to a file called "useful command line's" so that I don't have to ever ask about the same thing twice. 

Thanks.

---

### Post by Sweet Spot on 2007-05-18
Nuthin, hu ?  Sometimes I wonder....

---

### Post by maaronB on 2007-05-18
You can extract and play the game with out going to the command line.
If you are using regular ubuntu (Gnome version) just right click on the ActionCube_v0.92.tar.bz2 file.  Then click on Extract here.  

This will create an action cube folder, inside of that there will be a file called actioncube.sh.  Just click on that and you should be able to play.  If it doesn't work you are going to need to install some SDL libraries.  

Open synaptic and install libsdl-image1.2 and libsdl-mixer1.2.  (Synaptic can be found under the SYSTEM->Administration.)

---

### Post by maaronB on 2007-05-18
If you do want to use the Command Line you are basically doing the same thing.

First go to the directory it is in.  Assuming this is the Desktop just type ```
cd Desktop
```
Then extract the file. ```
 tar jxfv ActionCube_v0.92.tar.bz2
```
Then cd into the Actioncube directory.  ```
cd Actioncube
```
Then run the game. ```
sh ./actioncube.sh
```

If you get any errors that include any line like this. ```
error while loading shared libraries: libSDL_image-1.2.so.0:
``` then you need to install that library.  
using ```
sudo aptitude install <library>
```


Everything else discussed was about making a launcher(in windows speak a desktop Shortcut) for the game, but I think you should try and get it running before worrying about that.

---

### Post by Sweet Spot on 2007-05-19
Thank you for the help guys. Unfortunately, it's not working. To note, I already had the SDL library files installed (both. Just not the dev ones, which I don't need anyway, right ?) 

When I click on the .sh file (which I should have said, I've done before with the same results as now) it opens Gedit and here's what I see:

> /bin/sh
# CUBE_DIR should refer to the directory in which Cube is placed.
#CUBE_DIR=~/cube
#CUBE_DIR=/usr/local/cube
CUBE_DIR=./

# SYSTEM_NAME should be set to the name of your operating system.
#SYSTEM_NAME=Linux
SYSTEM_NAME=`uname -s`

# MACHINE_NAME should be set to the name of your processor.
#MACHINE_NAME=i686
MACHINE_NAME=`uname -m`

case ${SYSTEM_NAME} in
Linux)
  SYSTEM_NAME=linux_
  ;;
*)
  SYSTEM_NAME=native_
  ;;
esac

case ${MACHINE_NAME} in
i486|i586|i686)
  MACHINE_NAME=
  ;;
*)
  if [ ${SYSTEM_NAME} != native_ ]
  then
    SYSTEM_NAME=native_
  fi
  MACHINE_NAME=
  ;;
esac

if [ -x ${CUBE_DIR}/bin_unix/native_client ]
then
  SYSTEM_NAME=native_
  MACHINE_NAME=
fi

if [ -x ${CUBE_DIR}/bin_unix/${MACHINE_NAME}${SYSTEM_NAME}client ]
then
  cd ${CUBE_DIR}
  exec ${CUBE_DIR}/bin_unix/${MACHINE_NAME}${SYSTEM_NAME}client -w1024 -h768 $*
else
  echo "Your platform does not have a pre-compiled Cube client."
  echo "Please follow the following steps to build a native client:"
  echo "1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed."
  echo "2) Change directory to source/src/ and type \"make install\"."
  echo "3) If the build succeeds, return to this directory and run this script again."
  exit 1
fi

Also, when I attempt to cd actioncube, I get: "No such file or directory", which I don't understand but..whatever. 

The Gedit quote, says I need SDL, SDL image and SDL mixer. two of which I"m SURE I have, but which is the image ?  I'm also confused about what I have to do in step # 2. What does that mean exactly ? I tried Cd'ing to source/src, but that yields nothing. Sorry for being the ultimate nooberton here guys... 

Doug

---

### Post by MonkeyBoy on 2007-05-19
If at first you don't succeed...cheat.

Go to this page:

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

Actioncube is the third game down at time of writing.  Click on the Actioncube-data link and choose to install with GDebi Package Installer.  It will take a few mins to download then will show a box asking if you want to install.  Click install.  Then do the same with the Actioncube link on the website which will be a lot faster.

Once you have installed both files in the correct order you will find that there is a nice copy of Actioncube in your games menu!  :D

---

### Post by DoktorSeven on 2007-05-19
> **Sweet Spot said:**
> Thank you for the help guys. Unfortunately, it's not working. To note, I already had the SDL library files installed (both. Just not the dev ones, which I don't need anyway, right ?) 

When I click on the .sh file (which I should have said, I've done before with the same results as now) it opens Gedit and here's what I see:


Right-click the .sh file, Permissions tab, check "Allow executing file as program."  Double click it; if you get a popup asking if you want to run or view, click Run.

---

### Post by Sweet Spot on 2007-05-20
> **MonkeyBoy said:**
> If at first you don't succeed...cheat.
 
Go to this page:
 
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)
 
Actioncube is the third game down at time of writing. Click on the Actioncube-data link and choose to install with GDebi Package Installer. It will take a few mins to download then will show a box asking if you want to install. Click install. Then do the same with the Actioncube link on the website which will be a lot faster.
 
Once you have installed both files in the correct order you will find that there is a nice copy of Actioncube in your games menu! :D
 
Yeah, actually that was the first way I tried it. Apparently they're not keeping up with the Dapper build, as the only one they have is for Feisty. So, no worky. :(  (You ever read the Great And Secret Show, by Clive Barker...Monkey Boy ? )
 
Thanks Doktor, I'll try that when I get home. Sounds ALMOST promising ! ;)

---

### Post by maaronB on 2007-05-20
> When I click on the .sh file (which I should have said, I've done before with the same results as now) it opens Gedit and here's what I see:


For some reason you are reading the file instead of executing it.  I don't know why that would happen so I can't really help.  I hope what DoktorSeven said works.

> Also, when I attempt to cd actioncube, I get: "No such file or directory", which I don't understand but..whatever. 

the name of the directory is ActionCube and capitalization does matter in linux.
so the command is actually ```
cd ActionCube 
```

If it still doesn't work the ```
ls
``` command lists the files and directories in the current directory.

Also when typing in the name of a file or directory you should know about  Tab completion.  Pressing the Tab key will automatically complete the name you are typing.
For instance instead of 
cd Desktop
cd ActionCube
type 
cd Des[TAB] 
cd Act[TAB]
Doing it that way will help avoid spelling mistakes.  As long as you can get the first couple letters right you shouldn't have any problem.

---

### Post by Sweet Spot on 2007-05-20
Pretty darned useful information there MaaronB, thanks ! 
And for the record Dok, your suggestion was useful as it SORT of worked ! Well, I got AC working, but for future reference, it's not the .sh file which needs to have the permissions changed, but rather, in Nautilus there's a tab in preferences, which is called 'behavior', and within that is a list of choices for "execution of text files'. I chose to set it to "ask every time", which then gives the option to run the file. 

So yes, thank you for that, since I knew there was some way to change that behavior, even though the option wasn't in the permissions tab of the .sh file. 

Now the only problem is, I wish I liked ActionCube more ! :)  It's "ok", but so far from really decent... I don't mind team based games so much, but there's really nothing BUT team based capture the flag or one shot and you're dead games... pretty dull choices to work with. And the maps are kind of small... 

I was really looking for a game that is similar to Raven Shield. I really loved that game (played in Windows) a lot. Had a great choice of weapons, maps and tactical layouts. And it was a snap to set up your own server and modify the rules to your liking... Tons of fun. 

Should I ask here how to set up the .run file for Tremulous ?  I've no clue with this one.

---

