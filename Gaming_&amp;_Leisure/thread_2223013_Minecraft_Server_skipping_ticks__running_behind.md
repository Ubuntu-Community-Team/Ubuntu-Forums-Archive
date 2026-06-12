---
title: "Minecraft Server skipping ticks / running behind"
date: 2014-05-09
forum: Gaming &amp; Leisure
---

### Post by sean40 on 2014-05-09
Hello and i want to say in advance if there is a solution already out there please point me to it as i have looked on the forums here for about an hour and tried everything i know of. I haven't found a solution so far.

I come to you all for help Please.

1. Specs:
  Software:
    java version 1.7.0 update 55
    OpenJDK Runtime Envirement (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu~0.12.04.2)
    OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)
    minecraft bukkit server 1.7.2 0.3R build 3020
    ubuntu 12.04 LTS 64bit OS
  
  Hardware:
    128 Samsung Pro SSD
    Xeon 1240v3 4 Cores/ 4 Threads @ 3.40GHZ
    16GB ECC RAM by Crucial @ 1600MHZ
    Dual Gigabit Ethernet network adapter

2. the problem:
  as i am in game on my gaming rig when im running around, pigs / chickens in game pc skip around and when i look at the logs the server is saying: "Running XXXms behind, skipping XXX tick(s)"

3. what i tried:
  i tried uninstalling java and installing the default java 1.6 but the issue i have with java 1.6 is that 1.6 java doesnt load the plugins i have properly
  i tried doing an entire server reboot

4. Questions im asking:
  does the lwjgl have anything to do with server side ubuntu?
  if i need to update the lwjgl, where are the files stored?
  is there a memory leak? (using parameters in java -Xmx3G) <- i think this should be plenty for a small server


the most recent log file
```
[01:40:15] [Server thread/INFO]: XXXXXXXXXXX lost connection: You have been idle for too long!
[01:40:15] [Server thread/INFO]: XXXXXXXXXXX left the game.
[01:40:40] [Server thread/INFO]: XXXXXXXXXXX[/192.168.1.2:50452] logged in with entity id 484082 at ([world] -419.6337687853921, 80.0, -379.69944865887913)
[01:41:39] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 6295ms behind, skipping 125 tick(s)
[01:41:52] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 2023ms behind, skipping 40 tick(s)
[01:47:49] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 2053ms behind, skipping 41 tick(s)
[01:52:50] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 2705ms behind, skipping 54 tick(s)
[01:53:41] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 2126ms behind, skipping 42 tick(s)
[01:54:02] [Server thread/WARN]: Can't keep up! Did the system time change, or is the server overloaded? Running 5674ms behind, skipping 113 tick(s)
[02:01:08] [Server thread/INFO]: XXXXXXXXXXX lost connection: Disconnected
[02:01:08] [Server thread/INFO]: XXXXXXXXXXX left the game.
[02:02:26] [Server thread/INFO]: CONSOLE: Stopping the server..[m
[02:02:26] [Server thread/INFO]: Stopping server
[02:02:26] [Server thread/INFO]: [Sleeper] Disabling Sleeper v1.2.2
[02:02:26] [Server thread/INFO]: Saving players
[02:02:26] [Server thread/INFO]: Saving worlds
[02:02:26] [Server thread/INFO]: Saving chunks for level 'world'/Overworld
[02:02:26] [Server thread/INFO]: Saving chunks for level 'world_nether'/Nether
[02:02:27] [Server thread/INFO]: Saving chunks for level 'world_the_end'/The End

```

---

### Post by dannyboy79 on 2014-05-09
i run my own minecraft server as well. the hardware i run it on is probably half yours (A8-3870k with 4GB DDRIII 1600Mhz ram) and despite getting the error messages in my server log about not being able to keep up i don't experience any mob skipping or weirdness like that. Within your date/time setting are you sync'd with a time server (referred to as NTP)? I don't know what you're talking about when you mention "lwjgl"
3GB allocated for minecraft should be plenty for minecraft, i only use 2048M to run my server but then again it depends how many mods you're running. i am only running a vanilla server. My friends runs a heavily mod'd bukkit world and he allocates 16GB of ram out of his total 32GB in his  machine. Here's the command options i use, see if using these helps
```
java -Xms2048M -Xmx2048M -Djava.net.preferIPv4Stack=true -XX:MaxPermSize=128M -XX:UseSSE=3 -XX:-DisableExplicitGC -XX:+UseParallelOldGC -XX:ParallelGCThreads=4 -XX:+AggressiveOpts -XX:+UseCompressedStrings -jar minecraft_server.jar nogui
```
the IPv4 is so that it prefers IPv4 connections over IPv6 and the rest are just java optimizations

---

### Post by sean40 on 2014-05-09
thank you for your quick response dannyboy79.

as of now the server is really lightweight, only 2 plugins and no mods on it. ive done a crontab to update the ntp daily as since the last reboot the ntp was only in difference of -.03877 sec pretty small so i dont think the ntp and the minecraft server is an issue.

and as for your command line ive copied it into a start.sh script because of its length and the minecraft starts up just fine, but a little slow (4.998)s to load the server where ive noticed it usually takes about to or less than 1 second.

do you think the java version im using isnt reliable?

and to answer your question about the [COLOR=#000000]lwjgl it stands for (LightWeight Java Game Library)
this is used to run minecraft, but im not sure if the lwjgl is even used for a headless minecraft server

[/COLOR]

---

### Post by dannyboy79 on 2014-05-09
my minecraft server isn't headless (it does have an X server running on it ) but I run the java command with nogui and i don't use lwjgl so I doubt you need it. i am not sure what java version i am using on my server, i'll have to check but i think it's whatever is in the repositories. I am running xubuntu 14.04

the server taking a little longer to start is most likely due to the extra java options and shouldn't matter once it's up and running

---

### Post by sean40 on 2014-05-10
well i got it to work more smoothly than normal, i ended up trying oracle java 7 and that did not help so i had to trash and get rid of that. I ended up using the openJDK-java7-jre-headless which is a package listed by apt-get and this one seems to be running smother.

not as smooth as i would like but it has not been skipping ticks on login or while people are playing on the server.

ill leave this open for anyone else throwing in ideas on their builds and what they are using to run their servers

---

### Post by dannyboy79 on 2014-05-10
that's the same version i am running

---

