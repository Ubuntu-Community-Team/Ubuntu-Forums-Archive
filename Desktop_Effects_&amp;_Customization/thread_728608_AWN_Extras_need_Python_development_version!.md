---
title: "AWN Extras: need Python development version?!"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by steak-sandwich on 2008-03-19
Okay, I'm trying to install AWN EXTRAS the entire day. 
First, I looked at the official website and did what they say. I was able to install AWN. 
I downloaded AWN EXTRAS 0.2.6 and tried to compile in. When I type in ./configure, I get the following message

> all checkings..........
checking python extra libraries...  -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic
checking consistency of all components of python development environment... no
configure: error:
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================


I don't know where to get this development version. 
Then I looked in this forum. I found all the How-To threads, but always something is missing.

For instance, I used this instruction
[http://ubuntuforums.org/showthread.php?t=561810&highlight=awn+extras](http://ubuntuforums.org/showthread.php?t=561810&highlight=awn+extras)
when I type in > bzr co [http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk) awn-extras
it starts to download the files, but I can't do the next step > cd awn-extras/awn-applets/awn-core-applets/ because the folder is not there.

After more than 12 hours I'm getting tired, especially my eyes. 

Can someone help me with this problem?

---

### Post by unabatedshagie on 2008-03-19
[LIST=1]
[*]Download and install the [dependencies](http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix) for awn extra's
[*]run ```
bzr branch lp:awn-extras awn-extras
```
[*]cd into awn-extras
[*]run ```
./configure && make && sudo make install
```
[/LIST]
That should do it.

If you have any problems then try the [wiki](http://wiki.awn-project.org/Awn_Extras:Installation) page.

---

### Post by steak-sandwich on 2008-03-19
okay now I have another problem. 
I want to uninstall everything to start from scratch. I removed everything from the Synaptic Package Manager. AWN didn't work properly. It stopped showing all the open applications (launchers). I don't know what happened. However, I uninstalled it, and installed it from source. Everything worked, but apparently I didn't uninstall everything because I still have the same problem. All the themes were still there and it doesn't show me the launcher though they are in the list. 
Now I uninstalled it again by > make uninstall

I am not really a newb but still learning the whole thing.

THX

Ben

---

### Post by unabatedshagie on 2008-03-19
You could try manually deleting the folders

Here's a list of default install locations (you might want to manually check those files and folders exist before running the commands)

```
sudo rm -r /usr/local/bin/awn-manager
sudo rm -r /usr/local/bin/awn-applet-activation
sudo rm -r /usr/local/lib/awn
sudo rm -r /usr/local/lib/libawn*
sudo rm -r /usr/local/lib/python2.5/site-packages/awn
sudo rm -r /usr/local/share/avant-window-navigator
sudo rm -r /usr/local/share/awn-extras-applets
sudo rm -r /usr/local/share/awn-core-applets
sudo rm -r /usr/local/include/libawn
```

That should pretty much kill avant and allow you to start from fresh

---

### Post by steak-sandwich on 2008-03-19
okay I tried to do that 
```
./configure && make && sudo make install
```
then it says 
> bash: ./configure: No such file or directory

what the hell is wrong with my computer?

---

### Post by steak-sandwich on 2008-03-19
okay I downloaded the source code from the website and then it works. but don't ask me why there is no configure file when I try to do it your way

---

### Post by moonbeam on 2008-03-21
> **steak-sandwich said:**
> okay I tried to do that 
```
./configure && make && sudo make install
```
then it says 


what the hell is wrong with my computer?

You probably checked out a branch of trunk using bzr.  When the source is checked from trunk then it is necessary to run  'autogens.h' instead of 'configure'  (autogen.sh actually creates the configure script and executes it)

If you download a source release (a tarball) then there is a configure script available in the downloaded source.

So... probably nothing wrong with your computer :-)

---

