---
title: "Minecraft 1.8 Stopped working after java update."
date: 2015-04-24
forum: Gaming &amp; Leisure
---

### Post by colmeweb on 2015-04-24
So when I woke up this morning my computer ran a java update and then I tried to run my Minecraft .jar and all it did was open the archive manager. 
The file is still marked to allow executing as program. I have spent about an hour going over the forum and trying to make this work but nothing is working. 
If anybody has had luck it would be great. 

I am currently running 14.10.

P.S. I also got the prompt to upgrade to 15.04 today, I haven't done it because I usually wait a month or so for the bugs to get worked out. If anybody thinks it would help I am always willing to give it a shot.

---

### Post by efflandt on 2015-04-25
I read something somewhere that an update may have broken running a jar from whatever file viewer by double clicking it (maybe for security reasons). Have you tried running it from a terminal? **cd** to the directory it is in then do: **java -jar Minecraft.jar**

If that works you could write a simple shell script to cd to the directory and launch the minecraft launcher. Put the script in a ~/bin directory, if that does not exist, create it (mkdir ~/bin) and once you logout/login that ~/bin directory will be in your $PATH. Make sure that the script has execute permission.

Personally I use a desktop launcher to launch minecraft. Desktop launchers are created with **Main Menu**, also known as **alacarte** package. But that does not expand shell metacharacters (like ~/) or sometimes command line parameters unless you use something similar to this:```
sh -c 'java -jar ~/Downloads/Minecraft.jar'
```

---

### Post by colmeweb on 2015-04-25
Update / Self Bump

I tried:
@C850D:~/Games$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

but got this as a result:
Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
Error: Could not find or load main class net.minecraft.LauncherFrame

If anybody knows how to load net.minecraft.LauncherFrame or whatever that program is it might solve my problem.

---

### Post by colmeweb on 2015-04-25
I tried your suggestion but got this response.

Error: Unable to access jarfile /home/colin/Games/minecraft.jar

If you know how to get around this, or a re-install that doesn't require a .jar file that would be great.

Thanks for the suggestion.

---

### Post by efflandt on 2015-04-25
Note that unlike Windows, file names are case sensitive in Linux. So minecraft.jar is not Minecraft.jar.

Memory sizes and LauncherFrame were an old method that was used for the old **minecraft.jar** (little m) launcher (which is NOT the minecraft.jar in ~/.minecraft). That does not work for the current **Minecraft.jar** (big M) launcher which simply uses **java -jar Minecraft.jar** (or path_to/Minecraft.jar)

---

### Post by colmeweb on 2015-04-26
It worked, and sorry about the stupid typo on my first attempt.
When I ran it I got this:

```
 @Satellite-C850D:~$ sh -c 'java -jar ~/Games/Minecraft.jar'Picked up JAVA_TOOL_OPTIONS: -javaagent:/usr/share/java/jayatanaag.jar 
Current proxy version: 7
Gotten proxy version: 7.0
New launcher not downloaded
p: /127.0.0.1:60134
[21:04:04 INFO]: Minecraft Launcher null (through bootstrap 4) started on linux...
[21:04:04 INFO]: Current time is Apr 25, 2015 9:04:04 PM
[21:04:04 INFO]: System.getProperty('os.name') == 'Linux'
[21:04:04 INFO]: System.getProperty('os.version') == '3.19.0-15-generic'
[21:04:04 INFO]: System.getProperty('os.arch') == 'amd64'
[21:04:04 INFO]: System.getProperty('java.version') == '1.7.0_21'
[21:04:04 INFO]: System.getProperty('java.vendor') == 'Oracle Corporation'
[21:04:04 INFO]: System.getProperty('sun.arch.data.model') == '64'
[21:04:04 INFO]: proxy == SOCKS @ /127.0.0.1:60134
[21:04:05 INFO]: JFX has been detected & successfully loaded
[21:04:12 INFO]: Refreshing local version list...
[21:04:13 INFO]: Refreshing remote version list...
Proxy - onConnect - GET http://s3.amazonaws.com/Minecraft.Download/versions/versions.json
[21:04:13 INFO]: Refresh complete.
[21:04:16 INFO]: Loaded 1 profile(s); selected
[21:04:16 INFO]: Refreshing auth...
[21:04:16 INFO]: Logging in with access token
Proxy - onConnect - POST http://authserver.mojang.com/validate
Proxy: Authserver
Proxy postedJSON: {"clientToken":"06ee0e47-f433-4f35-a413-87cc72090475","accessToken":"a6b2362dabc331949ed1bb79bd530d4b"}
 
```

So apparently the new launcher didn't download with the last update.

One last thing, since I have never made a script before could you point me to thread / tutorial on how to set it up.

Thanks for everything.

---

### Post by efflandt on 2015-04-26
For a shell script it is best to put them in a **bin** directory in your home directory, because once you have logged out and logged back in, that ~/bin will automatically end up in your $PATH, so you can simply type the script name to run it without needing an path to the script. If you have not made a bin directory you can create it with```
mkdir ~/bin
```The next time you login, that will be in your $PATH (echo $PATH). Write the script with a text editor and save it to that bin directory. Give the file execute permission either using the file manager, right clicking, select Properties > Permissions and marking the Execute box at the bottom, or in a shell by doing **chmod +x scriptname**. Then you should be able to run the script by just typing its name without any path.

The first line of a script called a shebang line (for the #!) tells the shell what should be used to interpret a script. The #! should be at the beginning of the first line, but space(s) or not do not matter between that and path to the interpreter. The first line of a simple shell typically uses **#!/bin/sh** which would use a slimmer shell than bash called dash. If you specifically need something bash can do, but dash cannot, you could use **#!/bin/bash**

Anything after # in any other line is a comment that is not executed.

Then you enter lines with any commands you want to run, anything from a single command line with a bunch of standard paths and parameters, multiple commands if you want to do a sequence of things, or more complicated scripts that loop and/or make decisions. For example this is a script to run a minecraft server:```
#!/bin/sh
# Change cd line to your path to minecraft_server.jar
cd ~/Minecraft-server
java -Xmx3G -Xms3G -jar minecraft_server.jar nogui
```If you want to make a desktop shortcut, click on Dash (Search your computer and online sources) icon at top of Unity bar on left and search for Main Menu. Once you add **New Item** there, log out of X and log back in, you can launch your program from Dash. And while it is running you could right click on its icon in Unity bar and **Lock to Launcher**.

---

