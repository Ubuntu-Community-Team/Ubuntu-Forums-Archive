---
title: "Mupen64PLus"
date: 2013-12-15
forum: Emulators
---

### Post by MattKimura on 2013-12-15
My info:
OS: XFCE raring
Device: Chromebook Acer C720




Lately I've been successfully figuring out how to compile, or get the latest repos for emulators, installing the latest builds and such. But one emulator gives me so much trouble. Mupen64Plus. The N64 emulator best for Ubuntu. 


I first added a PPA, from Sven Ecklemann. This installs Mupen64Plus 2.0, but now I don't know how to use it after.


I understand that there's no GUI, and you're forced to use the terminal for it.
So in terminal, I type "mupen64plus [Rom directory and rom name]" But I get an error, it doesn't want to load the z64/v64 file. The roms are in my flash drive in a folder. 


I then tried downloading the source of the latest build, but dear god it's complicated. I have no idea how to build it. 


I'm basically stuck, to asking questions. Searching usually gives me results I'm not looking for. Any help running this emulator would be appreciated.


Wine with Project64 is not an option, the games run at unplayable speeds. Though Wine does work with Mupen64 0.5.1, which is really ancient. 2005 vs 2013




Also, I had no luck getting a frontend to work, after installing mupen64plus.
I installed m64py frontend, and when I launch it, nothing happens. My main concern is to get Mupen64plus working, with a frontend of any kind.
This fight seems to be for nothing, Banjo Tooie crashes, and zelda majora's mask crashes occasionally too. Paper Mario has flickering. This is what's shown on the compatibility list.

---

### Post by deadflowr on 2013-12-15
I'm not sure, but I think you need to run the saveoptions first
Look at the help options first, 
```
mupen64plus -h
```
and set whatever parameters you want. 
Then
```
mupen64plus --saveoptions
```
I believe this generates the config file.
The config file is located in /home/user/.config/mupen64plus/mupen64plus.cfg
You can look it over and make sure the controller settings and plugins are listed, and/or listed correctly.
When that's all taken care of run try running a romfile again
```
mupen64plus /full/path/to/filename
```
I find running the full path name of the rom to work best.
So if it's on a flash drive, the path is most likely to be /media/something(whatever the flash drive is called)/filename.

---

### Post by mips on 2013-12-15
GUI [https://bitbucket.org/auria/wxmupen64plus/wiki/Home](https://bitbucket.org/auria/wxmupen64plus/wiki/Home)

---

### Post by BigSilly on 2013-12-15
Yes, and [M64Py]("http://m64py.sourceforge.net/") is another good one.

---

### Post by MattKimura on 2013-12-16
Thanks for the reply, I appreciate it. Out of everyone on other sites, you've been supportive.

Mupen64plus just doesn't want to work. It fails to load any rom files. I can't even use a parameter.
When I enter: mupen64plus --saveoptions
(Or any parameter)
It says that it fails to load rom. But Im not loading any roms here o_0

So then I tried this: mupen64plus /home/matt/desktop/Super Mario 64.v64
But it says that Super, Mario, and 64 are incorrect commands.
So then I tried the same command, this time without spacing out the rom file name like so: SuperMario64.v64
And it just says it can't load the rom. This rom is indeed legit, it worked on my desktop computer perfect. 
Yes I moved this specific game to my desktop to see if my flash drive was the problem for not being able to load games.

On the otherhand, I tried to use retroarch to use mupen64plus on it, but that emulator also fails at loading roms. That goes for any rom.
I load up the mupen64plus dynamic core in retroarch, then load a rom. But everything goes bad from there. Here's the error I get for retroarch: [http://pastebin.com/vTA0Yx2w](http://pastebin.com/vTA0Yx2w)

I can indeed find my mupen64 config file in: /.config/mupen64plus/mupen64plus.cfg
everything seems fine in it. I'm still at a fresh install of Mupen64plus, no options changed. The UI works fine, I can even have mupen64plus show me the list of parameters, so the emulator is loading up fine. I just can't figure out the error, shouldn't it work right away? This is the most complex emulator I've used. retroarch being the 2nd.

As for frontend GUI's, all of them seem complicated to use. M64PY has an installer, and creates a shortcut file. But nothing happens when you load it. As for Wxmupen64plus, I have no idea how to access it after installing it. Then I can't figure out how to install Wxwidgets, which is required to run Wxmupen64plus. There's zero instructions on their site, the linux/ubuntu field is cruel like that. Nothing wants me to get N64 emulators working. My only hope is mupen64 0.5, which works surprisingly good. Just not with my favorite games like Banjo Tooie which crashes. Was hoping to use a more updated emulator that can handle it better.

---

### Post by deadflowr on 2013-12-16
Try using the quotes method for the file path
```
mupen64plus "/home/something/something/my game.something"
```

---

### Post by MattKimura on 2013-12-17
Wow thanks a lot, that worked perfect. 
I know why it was shooting out errors. It was the spaces in the file path. Any kind of space is considered a new command. 
You solved my issue, I appreciate it!

But as a side question, how would I set a parameter without spacing? Do I add the quote around the entire command?
"mupen64plus --gfx mupen64plus-video-glide64mk2 /media/removable/USB Drive/Emulators/N64/game name.z64"

Do I have to set the gfx plugin every time I launch a game, or just one time? 

I'm creating launchers for each game, I'm wondering if I have to set a parameter between the command.

Also, how do I choose where the save files are, or is there a default directory for them already?

---

### Post by dannyboy79 on 2013-12-17
i happily use M64Py version 0.1.0. You shouldn't need the quotes around the entire command, only the path and filename when the game name has a space in it's name because the various parameters shouldn't have any spaces in them to begin with. Linux/Unix hates spaces and developers know this so they wouldn't code in a parameter which has a space

---

### Post by deadflowr on 2013-12-17
> **MattKimura said:**
> 
Do I have to set the gfx plugin every time I launch a game, or just one time? 

I'm creating launchers for each game, I'm wondering if I have to set a parameter between the command.

Also, how do I choose where the save files are, or is there a default directory for them already?

If you're going to create launchers, then set any extra parameter per launcher.
I usually set my basic parameter settings(like resolution and maybe default plugin here or there)and issue the --saveoptions command, which in turn save that as the default settings.
However, some games need extra workings, here and there, and in my created launchers I add those to their commands.
But I also use unity and as such utilize the quicklist feature, so my launchers have various options, like loading the game in fullscreen or window mode, without having to press any extra buttons when it loads.
I would suggest looking into making aliases for the extended command, if you want to load the game through the command line.
[http://www.howtogeek.com/73768/](http://www.howtogeek.com/73768/)
The default save location is in /home/user./local/share/mupen64plus/save.
Here's the default kayboard layout
[https://code.google.com/p/mupen64plus/wiki/KeyboardSetup](https://code.google.com/p/mupen64plus/wiki/KeyboardSetup)
and here's the key listing that it uses
[http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h](http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h)
These can be changed in the mupen64plus.cfg file in the .config folder.

Edit: so today I decided to play some on my trusty install, and as it happens the version for trusty is 2.0.
As such, it has a newer config file and has this added line
```
#Controller configuration mode: 0=Fully Manual, 1=Auto with named SDL Device, 2=Fully automatic
mode = 2
```
this made the config reset the keybinding to the default state.
setting the mode to = 0 seems to have fixed that.

---

### Post by MattKimura on 2013-12-17
It's very difficult to get help with this emulator elsewhere, thanks for being so persistant to help me on this.

Those links were useful, I saved a screenshot of the controls and keyboard mappings for a later use if I ever need it.

I still can't figure out how to enter parameters though, I tried: mupen64plus--saveoptions    Without spaces and it doesn't work. I tried other parameters, I can't get them to work. I think this emulator is already using glide64mk2 on my end, since I can alt tab out of the emulator and see that the name of the process is glide64. Now I just want to enable fullscreen for every game, with maxed resolution (Fullscreen is enabled by default). My max resolution is 1366 x 780. which works perfect on all the other emulators.

Also, I tried the aliases trick, but nothing happens. I created agi, agu, and my own command named m64 which runs: mupen64plus "Directory"
But it tells me that it's not a valid command. Do I just type those words for it to work, or is there more to it?
Heres how I have it set up in a text file called .bash_aliases
[spoiler]
alias agi='sudo apt-get install'

alias agu='sudo apt-get update'

alias m64='mupen64plus "directory"'
[/spoiler]

Edit: The guide says to add the bash file in the home directory, but I think I was supposed to put that file in the main root directory. So that may be the problem with that.



My last mission is to connect a gamepad, or a PS3 controller via bluetooth as an input. Is it possible to do this with mupen64plus?
Seems like the only way to change input is within the cfg file. Which only shows keyboard mappings.

---

### Post by deadflowr on 2013-12-18
I've had a lot of fun playing around with this stuff.
Setting the parameters is simple
with plugins, it has a default directory (/usr/lib/x86_64-gnu-linux/mupen64plus for me at least)
so to switch the default plugin for example changing the video from rice to glide64
```
mupen64plus --gfx mupen64plus-video-glide64.so /path/to/game/file
```
notice that there is a space between mupen64plus and --gfx, and a space between the --gfx and the plugin. and plugin from the game filepath.
Likewise, if you wanted to run a plugin which is not in the default plugin directory, use the full path
something like
```
mupen64plus --gfx /some/other/path/other/than/the/default/plugin/path/mupen64plus-video-glide64.so /game/file
```
If you want to run multiple options like setting a cheat and fullscreen and a different plugin then
```
mupen64plus --cheats 1 --gfx mupen64plus-video-rice.so --fullscreen /game/filepath, or "/game/file path"
```
and so on, like so.
If you want to save it then add the --saveoptions command after the last option, but before the game file path.

So it's important to note the basics are option then space then option then space.

As far as setting up the controllers go, look at the file InputAutocfg.ini, which should be in either
/usr/share/mupen64plus, or
/usr/share/games/mupen64plus.

I see mine has a listing for a playstation3 controller, but I do not know how well it connects it.
This might help more on that matter
[https://code.google.com/p/mupen64plus/wiki/ControllerSetup](https://code.google.com/p/mupen64plus/wiki/ControllerSetup)

Overall though, I have had a little more fun playing around with this than I normally would care to do.
I normally just play the games, without getting into the underlying working of how to set thing up.
I hope something in the above ramblings help you, somewhat, out.
I'll leave with an interesting one
```
mupen64plus --cheats 'list' /game/file/path
```
if you run this command, if the game has cheats, which most certainly it will, it will generate the list, by number.
To enable the cheats run the cheats command and follow the basic one I used earlier.
If the cheat is something with extra options, like it says cheat number 1, subsection 3 then the command would be
```
--cheats 1-3
```
if you want multiple cheats then use commas between them
```
--cheats 1,2,3-4,5
```
and if you want to enable all cheats
```
--cheats 'all'
```

Again, I'm rambling.

---

### Post by MattKimura on 2013-12-19
Case closed! That post finished helping me, I'm finally set and pretty much understand how to work Mupen64Plus. 
I find that using windowed is better tan fullscreen, since fullscreen displays the same size anyways. It can never fill up the entire screen no matter what. --windowed --resolution 1024x768 is the best I can get.

I finally got all my game launchers created. I also added a shortcut to the saves folder, and the config file. I made screenshots of all the emulator controls, so I'm all set and don't even need a GUI or anything special. Just simply click a launcher and play.

But one thing was weird, the saves. I renamed my roms, deleting the "(U) [!]" parts of the file names. But no matter what I do, the output save files will always include "(U) [!]". So to import my save files to mupen64plus, I had to make a save file with every game to see how it's named. Then name my older save files accordingly. Now I have all my completed game saves from Project64. 
Oh and another thing, the save directory is now in the same directory as the roms. It creates a folder called saves, and that's where saves go. Though it seems like at one point, saves went to the default save directory. 

I can already see that Mupen64plus 2.0 works much better than Mupen64 0.5.1 . I'm glad I went through all this trouble to use a much more stable N64 emulator on my Chromebook. Hopefully I can help others now that I know how it works.

Thanks so much for your support, nobody else would've helped me with this.

---

### Post by bapoumba on 2013-12-21
Moved to Emulators.

---

