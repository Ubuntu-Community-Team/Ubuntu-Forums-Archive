---
title: "MonoDevelop 0.10 Released!!!"
date: 2006-04-05
forum: Desktop Environments
---

### Post by mattisking on 2006-04-05
Man, I hope we see MonoDevelop 0.10 make it's way into the Dapper repository. 

It looks very nice, particularly the addition of the Gtk# Forms Designer (stetic).

[http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.10]("http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.10")

---

### Post by JuanC on 2006-04-05
Good !!!

It comes with Visual designer for GTK#.

---

### Post by ember on 2006-04-05
Great news - I have been looking forward to this for quite a while. Actually I like C# pretty much and I am always happy to see the Mono project make progress.

---

### Post by Eklöf on 2006-04-05
Mono applications runs slower than a turtle walking backwards ! It just suck! :(

---

### Post by !nkubus on 2006-04-05
[QUOTE=Eklöf]Mono applications runs slower than a turtle walking backwards ! It just suck! :([/QUOTE]
But remember that Fable where the Turtle wins the race against the Rabbit

lol just joking

---

### Post by htinn on 2006-04-05
Wow, that had me confused. 0.9, then 0.10... okay.

---

### Post by guzerat on 2006-04-05
[QUOTE=htinn]Wow, that had me confused. 0.9, then 0.10... okay.[/QUOTE]

The "." is not a decimal point. The number after the point is the "smaller version" number of (in this case) version "0". 10 comes after 9. Quite logical :)

---

### Post by mattisking on 2006-04-05
[QUOTE=Eklöf]Mono applications runs slower than a turtle walking backwards ! It just suck! :([/QUOTE]

umm... I couldn't disagree more. Banshee, Muine, F-Spot, Beagle, Tomboy, Blam, MonoDevelop, MonoDoc, Cowbell, Diva, ...

---

### Post by g14 on 2006-04-05
[QUOTE=mattisking]umm... I couldn't disagree more. Banshee, Muine, F-Spot, Beagle, Tomboy, Blam, MonoDevelop, MonoDoc, Cowbell, Diva, ...[/QUOTE]
FYI: Tomboy applet takes about 12 seconds to start up when first logging into gnome for me. While it is doing that, it is blocking the rest of the panel making it annoying. I stopped using Tomboy for that reason. ymmv

---

### Post by sn123 on 2006-04-05
[QUOTE=JuanC]Good !!!

It comes with Visual designer for GTK#.[/QUOTE]
That's indeed nice, I've been using glade-gnome-2 till now for designing visual elements but have heard that stetic is better than glade-gnome..time to try it out :)

S

---

### Post by mattisking on 2006-04-05
[QUOTE=g14]FYI: Tomboy applet takes about 12 seconds to start up when first logging into gnome for me. While it is doing that, it is blocking the rest of the panel making it annoying. I stopped using Tomboy for that reason. ymmv[/QUOTE]

Yeah.. that's true Tomboy is slow but according to a few working on enhancing startup time for Gnome, this may or may not have anything to do with mono. I imagine it's slow because of the way it stores and loads it's notes. One small change that could help startup time would be to put the note loading in the first click/drop down of use or on a delayed timer to allow the plugin to load immediately and not delay startup.... but this is a reflection on tomboy, not mono.

---

### Post by nehalem on 2006-04-05
So can we expect it to hit dapper?  I would love this version for my stuff.

---

### Post by arpunk on 2006-04-05
[QUOTE=g14]FYI: Tomboy applet takes about 12 seconds to start up when first logging into gnome for me. While it is doing that, it is blocking the rest of the panel making it annoying. I stopped using Tomboy for that reason. ymmv[/QUOTE]
It takes only a few seconds, about 4 only...

---

### Post by Melvil on 2006-04-06
The delay is just because the mono runtime needs to be loaded, it's the same with java applications and the VM. But once it is loaded mono runs like a charm

---

### Post by trendzetter on 2006-04-06
I have been waiting for this release. Will this version be in the universe repositries ?

---

### Post by grozeille on 2006-04-06
I'm waiting for the update in the repository too...
But for now, I tried to "update" thanks to the addin manager, but it doesn't work. Then, I tried to install the rpm (alien -d :)). MonoDevelop is installed but crash before starting : System.Runtime.Remoting.RemotingException: Unix transport error.

Someone have an idea ? I'm the only one with this error ?
Thx.

---

### Post by jkarpago on 2006-04-07
I tried the same way and I get the same error.
Can anyone help, please?

---

### Post by shu on 2006-04-08
I've built 0.10 package and it is working good. You can find it here:

[http://users.vlo.gda.pl/~szuwarek/files/linux/monodevelop_0.10-1_i386.deb](http://users.vlo.gda.pl/~szuwarek/files/linux/monodevelop_0.10-1_i386.deb)

NOTICE: This package doesn't follow ubuntu naming rules, so you _have_ to remove all monodevelop packages before installing it. Similary you'll have to remove it if/when monodevelop 0.10 will hit official repositories.

---

### Post by brynjarh on 2006-04-08
[QUOTE=shu]I've built 0.10 package and it is working good. You can find it here:

[http://users.vlo.gda.pl/~szuwarek/files/linux/monodevelop_0.10-1_i386.deb](http://users.vlo.gda.pl/~szuwarek/files/linux/monodevelop_0.10-1_i386.deb)[/QUOTE]

The package installes fine but when I run it it wont start and when I run it from a terminal I get "Cannot find mozilla installation directory. Please set MOZILLA_FIVE_HOME to your mozilla directory", anyone else having this problem?


EDIT:
I did **export MOZILLA_FIVE_HOME=/usr/lib/mozilla/** and it got rid of that problem.

---

### Post by samjam on 2006-04-08
Why would monodevelop need to know where mozilla was?

---

### Post by clast on 2006-04-08
export MOZILLA_FIVE_HOME=/usr/lib/firefox

---

### Post by nzjrs on 2006-04-08
[QUOTE=Eklöf]Mono applications runs slower than a turtle walking backwards ! It just suck! :([/QUOTE]

Dont ruin the reputation of the ubuntu forums as helpful and flame free by posting rubbish like this

---

### Post by xrado on 2006-04-09
** (MonoDevelop:12925): WARNING **: The following assembly referenced from /usr/lib/monodevelop/AddIns/MonoDevelop.SourceEditor.dll could not be loaded:
     Assembly:   gtksourceview-sharp    (assemblyref_index=2)
     Version:    1.0.0.2
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/../AddIns).


** (MonoDevelop:12925): WARNING **: The class GtkSourceView.SourceLanguagesManager could not be loaded, used in gtksourceview-sharp, Version=1.0.0.2, Culture=neutral, PublicKeyToken=35e10195dab3c99f

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...

---

### Post by shu on 2006-04-09
Looks like you don't have gtksource-sharp installed.

---

### Post by sn123 on 2006-04-09
Is it just me whose mondevelop stopped working after recent upgrade? If I try to run monodevelop from the menu it crashes on startup and running it from console returns "Got a SIGSEGV while executing native code. Fatal Error". After looking at the stack trace, I found that it fails somewhere where it is trying to load Gecko libraries. So I set the MOZILLA_FIVE_HOME var to point to the fx directory and then it atleast monodevelop loads but if I try to run any existing apps that I wrote they crash randomly, any one else experiencing it?

EDIT: sorry my bad, had messed around with my existing app :D which was causing it to crash, the problem with the environment variable still remains though.

S

---

### Post by arpunk on 2006-04-09
[QUOTE=nehalem]So can we expect it to hit dapper?  I would love this version for my stuff.[/QUOTE]
Yea, i wonder if this release will made into dapper, its a nice release :D and a must need if you develop with mono/.net

---

### Post by sn123 on 2006-04-09
well few more things don't work for me, trying to add a new csharp file crashes monodevelop :( with error : "GLib-GObject-ERROR **: file gsignal.c: line 650 (emission_pop): should not be reached...aborting."
Wonder if somebody else is having this problem and any solution to get it working.

S

---

### Post by sn123 on 2006-04-11
[QUOTE=sn123]well few more things don't work for me, trying to add a new csharp file crashes monodevelop :( with error : "GLib-GObject-ERROR **: file gsignal.c: line 650 (emission_pop): should not be reached...aborting."
Wonder if somebody else is having this problem and any solution to get it working.

S[/QUOTE]
just upgraded to .10 and everything is now working hunky-dory...yay!

---

### Post by arpunk on 2006-04-12
```
Accepted monodevelop 0.10-0pre1ubuntu1 (source)
```
:)

---

### Post by jandante on 2006-04-12
how do we install that source package or should I wait till it's shown in synaptic

---

### Post by traherom on 2006-04-20
[QUOTE=jandante]how do we install that source package or should I wait till it's shown in synaptic[/QUOTE].10 is now in Synaptic!

However, I still have to set MOZILLA_FIVE_HOME in order to get it to start up... any ideas as to why?

---

### Post by jBilbo on 2006-05-07
Monodevelop 0.11 released!

[http://www.monodevelop.org/Release_notes_for_MonoDevelop_0.11](http://www.monodevelop.org/Release_notes_for_MonoDevelop_0.11)

---

### Post by brodock on 2006-05-09
ubuntu's mono is a way toooooooooooooooooooo slow.

after i updated to official mono i got lot's of speed increase (and also lots of more memory required to run apps)

---

### Post by !nkubus on 2006-05-30
I may sound stupid, but I installed Monodevelop 0.10 2 days ago on Dapper and when I double click on a .glade from inside of monodevelop it launches glade.. where is the visual designer? I see it in the plugins, but How do I use it?.


This is actually my 1st attemp on mono so sorry if I sound like a noob.

Thanks a lot for your help :)

---

### Post by jBilbo on 2006-05-30
Create a new GTK# project.

---

### Post by !nkubus on 2006-05-30
Yeah just saw that...

Now I feel stupid ](*,)

---

### Post by Melvil on 2006-05-31
```
greg@notey:~$ monodevelop

** (./MonoDevelop.exe:8496): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Components.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=10)
     Version:    2.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (./MonoDevelop.exe:8496): WARNING **: The class Gecko.WebControl could not be loaded, used in gecko-sharp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=ccf7d78a55e9f021

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted

```

Anyone else had this before? MD won't start due to this error.

---

### Post by jluckett79 on 2006-06-09
I'm new to Ubuntu and linux in-general but how long does it usually take a newer package like MonoDevelop 0.11 to show up in the repositories?  I know that I can download and install it separately but apt is a lot easier to work with (there may be other ways to install it easily that I'm just not aware of.)

Thanks in-advance!

John

---

### Post by fmo on 2006-06-09
I'd really like Mono and especially MonoDevelop to be more up to date on Dapper. I hope that someone listens ;-)

---

### Post by theh0g on 2006-06-18
Me too...somehow new versions of programs don't come to repos anymore :(

---

### Post by Melvil on 2006-06-18
You can install it easily from the official site

```
wget http://www.go-mono.com/download/noarch/monodevelop/0.11/monodevelop-0.11-0.novell.noarch.rpm
alien monodevelop-0.11-0.novell.noarch.rpm
sudo dpkg -i monodevelop-0.11-0.novell.noarch.deb
```

et voilá ;)

---

### Post by binks on 2006-07-18
> **Melvil said:**
> You can install it easily from the official site

```
wget http://www.go-mono.com/download/noarch/monodevelop/0.11/monodevelop-0.11-0.novell.noarch.rpm
alien monodevelop-0.11-0.novell.noarch.rpm
sudo dpkg -i monodevelop-0.11-0.novell.noarch.deb
```

et voilá ;)

ok so i uninstalled monodevelop 0.10 and install 0.11-0 like you said and it crashes every time i try to start it any ideas what i could of done
ps im not at home at the mo so i will start it in terminal and see if i get any errors.
cheers in hope binks

---

### Post by mattisking on 2006-07-27
I tried this as well... admittedly under Edgy. I got further. It fails to launch with a notification about basically not knowing where the mozilla libraries are. I also had problems with old configs so I removed them. You can do this by purging when using sudo apt-get remove xxxxxx --purge or in synaptic by choosing "Completely remove xxxxx" OR by manually deleting the config: rm -r ~/.config/MonoDevelop

You can "fix" the library problem:
export MOZILLA_FIVE_HOME=/usr/lib/firefox

though that isn't remembered and I believe is only within the terminal session. Launching monodevelop from this terminal then, gets me up and running but once I try to create a new project, big crash and out.

We're probably better off waiting on the new package, which is probably only going to happen in Edgy and/or Backports.

---

