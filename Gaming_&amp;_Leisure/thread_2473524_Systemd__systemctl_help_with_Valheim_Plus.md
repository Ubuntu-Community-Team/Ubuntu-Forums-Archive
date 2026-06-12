---
title: "Systemd / systemctl help with Valheim Plus"
date: 2022-04-06
forum: Gaming &amp; Leisure
---

### Post by motorhead102482 on 2022-04-06
I'm using  Ubuntu 20.04.4 LTS.  I'm having issues running a Valheim plus server as a service with systemd and systemctl.  I can get the service to run and I can load the game in, but for some reason it doesn't seem to pull save files from the right place.  I have a .service file setup to open a .sh file which has the file save location in the correct directory location.  If I stop the service and straight run the .sh file it works like it should.  If I run it as a service it acts like it can't see that information.  The other thing is if I play the game as a service it remembers what I was doing in the game when it was running as a service.  If I run it directly from the script, it remembers where I was in the game in that instance (two different points).  To me it seems like it's saving the game in a different place when ran as a service, but I can't figure out why or where.  The save files I expect it to use don't seem to be getting file updates when I look at the last save date/time on them if I run the game as a service.  I'm at a loss.  Thanks for any help in advance.


Here's the file path for the .service file:

```
/lib/systemd/system/BushwookiePVP.service
```


Here's the contents of the file:



```

[Unit]
Description=Valheim service
Wants=network.target
After=network-online.target

[Service]
Environment=SteamAppID=892970
Environment=LD_LIBRARY_PATH=/home/russ/Steam/ValheimPVP:$LD_LIBRARY_PATH
Type=simple
Restart=on-failure
RestartSec=10
KillSignal=SIGINT
Group=russ
WorkingDirectory=/home/russ/Steam/ValheimPVP
ExecStart=/home/russ/Steam/ValheimPVP/start_BushwookiePVP_bepinex.sh

[Install]
WantedBy=multi-user.target

```

Here are the contents of the .sh file above, but as I mentioned previously, it works fine if I just run it from CLI:

```
#!/bin/sh

# BepInEx running script
#
# This script is used to run a Unity game with BepInEx enabled.
#
# Usage: Configure the script below and simply run this script when you want to run your game modded.

# -------- SETTINGS --------
# ---- EDIT AS NEEDED ------

# EDIT THIS: The name of the executable to run
# LINUX: This is the name of the Unity game executable [preconfigured]
# MACOS: This is the name of the game app folder, including the .app suffix [must provide if needed]
executable_name="valheim_server.x86_64"

# EDIT THIS: Valheim server parameters
# Can be overriden by script parameters named exactly like the ones for the Valheim executable
# (e.g. ./start_server_bepinex.sh -name "MyValheimPlusServer" -password "somethingsafe" -port 2456 -world "myworld" -public 1)
server_name="Bushwookie PVP (V+ Mod)"
server_password=
server_port=2459
server_world="PVP Bushwookie"
server_public=1
server_savedir="$HOME/.config/unity3d/IronGate/Valheim"

# The rest is automatically handled by BepInEx for Valheim+

# Set base path of start_server_bepinex.sh location
export VALHEIM_PLUS_SCRIPT="$(readlink -f "$0")"
export VALHEIM_PLUS_PATH="$(dirname "$VALHEIM_PLUS_SCRIPT")"

# Whether or not to enable Doorstop. Valid values: TRUE or FALSE
export DOORSTOP_ENABLE=TRUE

# What .NET assembly to execute. Valid value is a path to a .NET DLL that mono can execute.
export DOORSTOP_INVOKE_DLL_PATH="${VALHEIM_PLUS_PATH}/BepInEx/core/BepInEx.Preloader.dll"

# Which folder should be put in front of the Unity dll loading path
export DOORSTOP_CORLIB_OVERRIDE_PATH="${VALHEIM_PLUS_PATH}/unstripped_corlib"

# ----- DO NOT EDIT FROM THIS LINE FORWARD  ------
# ----- (unless you know what you're doing) ------

if [ ! -x "$1" -a ! -x "${VALHEIM_PLUS_PATH}/$executable_name" ]; then
echo "Please open start_server_bepinex.sh in a text editor and provide the correct executable."
exit 1
fi

doorstop_libs="${VALHEIM_PLUS_PATH}/doorstop_libs"
arch=""
executable_path=""
lib_postfix=""

os_type=$(uname -s)
case $os_type in
Linux*)
executable_path="${VALHEIM_PLUS_PATH}/${executable_name}"
lib_postfix="so"
;;
Darwin*)
executable_name="$(basename "${executable_name}" .app)"
real_executable_name="$(defaults read "${VALHEIM_PLUS_PATH}/${executable_name}.app/Contents/Info" CFBundleExecutable)"
executable_path="${VALHEIM_PLUS_PATH}/${executable_name}.app/Contents/MacOS/${real_executable_name}"
lib_postfix="dylib"
;;
*)
echo "Cannot identify OS (got $(uname -s))!"
echo "Please create an issue at https://github.com/BepInEx/BepInEx/issues.
exit 1
;;
esac

executable_type=$(LD_PRELOAD="" file -b "${executable_path}");

case $executable_type in
*64-bit*)
arch="x64"
;;
*32-bit*|*i386*)
arch="x86"
;;
*)
echo "Cannot identify executable type (got ${executable_type})!"
echo "Please create an issue at https://github.com/BepInEx/BepInEx/issues."
exit 1
;;
esac

doorstop_libname=libdoorstop_${arch}.${lib_postfix}
export LD_LIBRARY_PATH="${doorstop_libs}":"${LD_LIBRARY_PATH}"
export LD_PRELOAD="$doorstop_libname":"${LD_PRELOAD}"
export DYLD_LIBRARY_PATH="${doorstop_libs}"
export DYLD_INSERT_LIBRARIES="${doorstop_libs}/$doorstop_libname"

export templdpath="$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH="${VALHEIM_PLUS_PATH}/linux64":"${LD_LIBRARY_PATH}"
export SteamAppId=892970

for arg in "$@"
do
case $arg in
-name)
server_name=$2
shift 2
;;
-password)
server_password=$2
shift 2
;;
-port)
server_port=$2
shift 2
;;
-world)
server_world=$2
shift 2
;;
-public)
server_public=$2
shift 2
;;
-savedir)
server_savedir=$2
shift 2
;;
esac
done

"${VALHEIM_PLUS_PATH}/${executable_name}" -name "${server_name}" -password "${server_password}" -port "${server_port}" -world "${server_world}" -public "${server_public}" -savedir "${server_savedir}"

export LD_LIBRARY_PATH=$templdpath
```

---

### Post by DuckHook on 2022-04-08
Welcome to the forums, motorhead102482.

You have good instincts posting with as much info as you have. However, your failure to wrap your output in [noparse]```

```[/noparse] tags made it unreadable. I tried to clean it up as best I could but I'm pretty sure that I left some artifacts and inconsistencies behind. In other words, the output above is not reliable.

When posting on the forums, you must wrap your output in [noparse]```

```[/noparse] tags. If you don't, forum software will do all sorts of unwanted things like inserting URL links and substituting smilies.

You may want to post the output again wrapped in  [noparse]```

```[/noparse] tags.

---

### Post by DuckHook on 2022-04-08
As to your problem, I've never played Valheim Plus and probably never will, so my help will only be limited, but here are a few things that come to mind:

Services run under root. Or at least they start out that way and will continue to do so unless they de-privilege themselves. Your scripts show no such de-privileging.

If you are new to Linux, then you should also note that running *anything* with root access is very dangerous, much less a game. It is a huge security risk and you must really be sure of what you are doing. A Linux newbie is unlikely to be familiar enough with the ecosystem to know what they don't know.

Now, if you actually *play* the game as a service, then you are playing as root. This is strictly a no&#8209;no. Never play any game as root.

The discrepancy between you launching the game using the .sh file and invoking it while it is running as a service now becomes clear. You are running the game in a proper unprivileged state under your normal user when invoking from its .sh file whereas you are running in a dangerous privileged state under the root user when invoking it as a service. Since these are different users, they save the game to different locations, neither of which are accessible to the other.

I don't understand why you are running the game as a service, especially when you can run it directly using its .sh script. You really should stop&#8594;unload&#8594;delete the service, delete all the cruft that this created (sorry, don't know how to help you with that one because I don't run Valheim Plus) and not do such things until you are fully familiar with the massive risks you are taking.

I'm assuming that you are new to Linux, but you may not be. However, in either case, the same warnings apply.

---

### Post by motorhead102482 on 2022-04-10
Thanks for the tips on the code tags.  I haven't used this site before, so I wasn't aware.  I would say I'm still beginner with linux and still learning the things I don't know as you mentioned.  So three things, this box is stand alone system with no other information other than my nickname for a home directory.  Also, this linux box is solely used for hosting a game server for this game.  Last, it is completely segregated from the rest of my network devices except for ssh from one machine and internet access.  So, I don't really care if the game has root access or not.  Considering I'm still learning Linux, may I ask for a suggestion?  The point of running it as a service was to easily start the service on reboot and start and stop it for updates.  Do you have another suggestion that would be easy and/or more privilege/system friendly?  FYI I did a find command starting in root directory to see if I could locate where the system could've been possibly saving those files with no luck.  If it is saving them in a root folder, I haven't been able to figure out where.  Thanks for your response and help.

Edit:  I guess my goal is/was to have the script open up automatically on reboot.  I would at some point like to include having it check for updates daily on its own, but I still haven't got there.  This is a pet project mostly just to help me learn how to operate linux.  The trials and tribulations of doing all of this from CLI has helped me learn alot.  I don't mind reading/searching articles, but sometimes it's hard to decipher what is "best practice" or more practical in terms of ways to execute things.

---

### Post by Tadaen_Sylvermane on 2022-04-10
There is a User field in systemd service files. That can run it as a given user I believe. 

```
[COLOR=#000000][FONT=&amp][Service]
[/FONT][/COLOR]Environment=SteamAppID=892970
Environment=LD_LIBRARY_PATH=/home/russ/Steam/ValheimPVP:$LD_LIBRARY_PATH
Type=simple
Restart=on-failure
RestartSec=10
KillSignal=SIGINT
Group=russ
User=russ
WorkingDirectory=/home/russ/Steam/ValheimPVP
ExecStart=/home/russ/Steam/ValheimPVP/start_BushwookiePVP_bepinex.sh
```

---

### Post by DuckHook on 2022-04-10
> **motorhead102482 said:**
> …I would say I'm still beginner with linux and still learning the things I don't know as you mentioned.
It's so rewarding to see someone starting out on their explorations of this awesome OS. You might find the links in my sig useful, especially the ones for newcomers.

The Internet is notorious for its inability to convey body language, so I want to state from the outset that what follows is in no way an attempt to hector or lecture you; it is just my clumsy attempt to impart general knowledge that you may not be aware of.
> …So, I don't really care if the game has root access or not.
Well, you should.

Linux is secure not by default, but because its users tend to be geeks who are more security conscious than the general population. It behooves us to adhere to good practice and to promote good computing hygiene for the collective good and not just for ourselves.

One of the most fundamental tenets of good practice in Linux is: ***always use least privileges.*** There is absolutely no reason to run a game with root privileges. Doing so is an open invitation to get pwned. Today, there are millions of nodes in botnet farms (running Linux) because their owners spun them up for various purposes (like games) but didn't implement good hygiene and did things such as running them as root. Please don't add to the problem by joining that crowd.

Tadaen_Sylvermane has posted a good, succinct example for de-escalating privileges. But this is only a start: the offered service file will make the game run as you.

My advice would be to go further: create a new user for the game that has even fewer privileges than you. For example, while you can elevate to root using sudo, there is no reason for a game to ever be able to invoke sudo.
> Considering I'm still learning Linux, may I ask for a suggestion?  The point of running it as a service was to easily start the service on reboot and start and stop it for updates.  Do you have another suggestion that would be easy and/or more privilege/system friendly?
 If you want to schedule system updates, this is already available using default system tools like *unattended&#8209;upgrades*. If there are other functions that you want to automate, again, there is no reason to allow this under a game account—it can be done separately on your own account using tools like cron.

The overall principle should now be getting clearer: *isolate* the game so that it can't escape strict confines that you set in advance. In security terms, this concept is called "sandboxing".

Please appreciate that a full discussion of security cannot be done in any forum thread. It's a massive topic that one will spend a lifetime learning and refining. A good place to start is our forum sticky: [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

It's an old sticky and some info is dated, but the general concepts are still sound.
> FYI I did a find command starting in root directory to see if I could locate where the system could've been possibly saving those files with no luck.  If it is saving them in a root folder, I haven't been able to figure out where.
The problem is that we don't know how your game installs, so we have no idea what file layout it creates. Root has its own directory under /. You can try looking there. Your game will have saved its game files to just about anywhere that its developers wanted. In Linux, running the game as root gave it free rein over your whole system. If this had not been run as root, then your saved games would likely be somewhere in your /home directory. This is not a given either. Some games install their save files in /var.

The power&#8209;users' tool for finding files is the *find* command. Read its *man* pages for details. Dozens of usage examples can be found online with an easy web search. A more user&#8209;friendly tool is *mlocate*. In the latest releases, *mlocate* has to first be installed. It doesn't come as part of the default install.
> I guess my goal is/was to have the script open up automatically on reboot.  I would at some point like to include having it check for updates daily on its own, but I still haven't got there.  This is a pet project mostly just to help me learn how to operate linux.  The trials and tribulations of doing all of this from CLI has helped me learn alot.  I don't mind reading/searching articles, but sometimes it's hard to decipher what is "best practice" or more practical in terms of ways to execute things.
Scripting is very powerful, but it must count as a more advanced topic. For your purposes, what is important is to distinguish between scripts that should run under very restricted confines (eg games) versus scripts that must run with root privileges (updates). These should not be conflated into the same user.

A few more general observations:

[LIST]
[*]You may not be as isolated as you think you are. If you are connected to the Internet and yet can ssh into this gaming server, then it is clearly on your own LAN. Anything that is on your LAN can attack anything else that is on your LAN. A well known attack vector is for malware to install itself on printers because few people update them, updates are mostly not even available and their security safeguards are primitive/nonexistent to start with.
[*]If you can ssh into this game server, then so can others. Make sure your ssh is set up properly permitting only keys and no passwords. Turn off root access. Confine ssh to only LAN IPs and nothing else, especially general Internet IPs. SSH is safe but only if configured properly.
[*]As you get more knowledgeable, you may wish to harden your sandbox even further using tools like apparmor. Yet another huge topic that needs a lot of background.
[*]A really advanced way to sandbox your game is to run it within a VM or, if that is not feasible due to resource limits, then to use some sort of container like Docker or LXD. I have another link in my sig dealing with LXD. These are very advanced configs with steep learning curves and I don't recommend them right now, given that you are just starting out, but IMO it's the ultimate way to properly sandbox things like game servers. Please save that for a future time when you are more familiar with Linux.
[/LIST]
Your desire to learn Linux is admirable and inspiring. I hope you keep at it and won't allow yourself to get discouraged by its learning curve. It's people like you who make it so rewarding to help out on these forums.

---

