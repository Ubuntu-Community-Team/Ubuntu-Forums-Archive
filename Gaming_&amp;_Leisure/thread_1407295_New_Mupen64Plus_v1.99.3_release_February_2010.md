---
title: "New Mupen64Plus v1.99.3 release February 2010"
date: 2010-02-15
forum: Gaming &amp; Leisure
---

### Post by argor on 2010-02-15
from  Richard42   [http://www.emutalk.net/showthread.php?p=429968#post429968](http://www.emutalk.net/showthread.php?p=429968#post429968)

> **Richard42 said:**
> The latest Mupen64Plus code, version 1.99.3, is now released!  For those of you who haven't been following our development saga, I'll spill some bytes explaining the re-archeticture that Mupen64Plus has undergone.  The biggest change is that Mupen64Plus is no longer an application; it is now a library, just like the plugins.  All of the user interface code has been removed from the emulator core and all of the plugins.  With the latest versions of Mupen64Plus, and extra component called a Front-end application is required; this program makes use of the Mupen64Plus emulator and attached plugins, and controls all non-game aspects of the User Interface.  This design has some big advantages: the user-interface application can be developed independently of the core emulator, the emulator itself is much simpler, and the code is more portable.  In fact, I have ported the emulator and plugins to Windows and it all builds perfectly in Visual Studio.

There are also a couple of temporary downsides to this re-design.  First, all of the old GUI code was completely removed (though it is still available through SVN).  The only Front-end application which I am releasing in the Mupen64Plus bundle is mupen64plus-ui-console, which is a command-line only program.  Fortunately it is quite usable, because the input plugin now supports auto-configuration for controllers that it recognizes, and even cheat codes are supported in the new command-line front-end.

The other side-effect of our re-architecture is that Mupen64Plus is no longer compatible with the older plugins.  The plugin API was changed and improved and going forward any plugin must be compatible with our improvements in order to be usable with Mupen64Plus.  I have upgraded and will be maintaining the following plugins: an SDL input plugn, an SDL audio plugin, the Hacktarux/Azimer RSP-HLE plugin, and the Rice video plugin.  These are all included with the Mupen64Plus release bundles.  Wahrhaft has also ported the Arachnoid, Z64, and (old) Glide64 video plugins, which are available in source form at: [http://bitbucket.org/wahrhaft/]("http://bitbucket.org/wahrhaft/").

I feel very confident about the quality of this Mupen64Plus release.  I believe that it's ready for general use by everyone and packaging for linux distributions.  I was ready to call this one 2.0, but I decided to hold off because there are a few longer-term developments still going on which may end up requiring changes in the API.  Since I want the final "2.0" API to be very stable, I thought it would be best to hold back and get this one out the door as another 1.99.x release, even though I feel it's read for the 2.0 name.  Here are the major changes since the last 'user' release, which was 1.99.1:

**Core Emulator Library**

[LIST]
[*] New feature: support for Gameshark 3.3 patch codes
[*] Lots of minor bugfixes
[*] Upgraded Plugin API to better handle errors and avoid crashes
[*] Win32 support
[/LIST]

**Audio Plugin**
[LIST]
[*] Completely re-wrote buffering/synchronization code to fix chopiness problems, allow better user control, and fix speed controller
[*] Win32 support
[*] bugfix: SDL volume control will always be used on systems without OSS support
[/LIST]

**Input Plugin**
[LIST]
[*] New feature: auto-configuration uses an .ini file instead of hard-coding the controllers in the source code
[*] Many new controller auto-configs, including original & 360 X-box, PS3, and others
[*] Better rumble support; several important bug fixes
[*] Win32 Support
[/LIST]

**Console Front-End Application**
[LIST]
[*] New feature: command-line option --set for setting arbitrary configuration variables
[*] updated MAN page for all the changes made in the 2.0 re-architecture
[*] Win32 support
[/LIST]

**Rice Video Plugin**
[LIST]
[*] New feature: compile-time option for opengl debugging
[*] bugfix: Many hi-res texture fixes
[*] bugfix: in ConvertImage.cpp none of the 4-bit conversion functions could handle 1-pixel wide textures
[*] Win32 support
[*] Several important makefile fixes
[/LIST]
*Detailed changelogs are available in the RELEASE files*

**Quick start (Linux)**
The easiest way to start running and testing this release is to download a binary bundle package from the Google Code site (link below), unzip it into a directory, and run it with this command: "./mupen64plus m64p_test_rom.v64".  You can run it directly from this directory, or to install it to your system, simply do "sudo ./install.sh".  Likewise, to un-install it, "sudo ./uninstall.sh"

**Quick start (Windows)**
For Windows users, download the bundle-win32 zip file from the Google Code site (link below) and unzip it to a directory.  Bust out your DOS prompt (Start->Run->cmd.exe or the "Command Prompt" in Start->Accessories).  Once you have the command-line window, 'cd' to the directory where you unzipped the win32 bundle.  Then run "mupen64plus-ui-console.exe mupen64plus.v64" to start up the test ROM.  Press Escape to exit.  Use the '--help' command-line option to get a list of all available options.  The last argument is always taken to be a path to an uncompressed N64 ROM image to run.  Sorry but there is currently no Windows installer available.

**Upgrading from previous 1.99.x releases**
Several of the configuration parameters have changed in the video and input plugins, so if you are upgrading from a previous 1.99.x release, you must delete your config file (located at ~/.config/mupen64plus/mupen64plus.cfg).

**You can help**
The Mupen64Plus team is focused on improving the quality and user-friendliness of our N64 emulator, and there are several important ways that people can contribute to this goal.
[LIST=1]
[*] Testing
For simple problems or help getting started, you can post here or join the developers in the #mupen64plus channel on irc.freenode.net.  For more serious problems, please report bugs on the [Google Code Issue Tracker]("http://code.google.com/p/mupen64plus/issues/list").
[*] Packagers
Packagers for Linux and BSD distributions are encouraged to help us reach your users by preparing Mupen64Plus packages for your distro.  We currently have packagers for the Arch Linux and Debian-based distributions.  I would particularly like to see packages for Gentoo and Fedora as well, though all others are welcome.  The 1.99.3 release includes quite a few changes to the build systems of the modules to assist packagers, and I believe that this release is ready for distribution.
[*] Front-end authors
The new Mupen64Plus architecture allows any interested developer to build their own front-end user interface application, using the language and GUI toolkit of your choice to drive the Mupen64Plus emulator.  Currently we have new GTK and Qt GUIs in the works, but they are very preliminary and have not been released.  If anyone would like to resurrect the old GTK or Qt GUIs from Mupen64Plus v1.5, I can give direction on the steps necessary to start this work.  This would be much easier than writing an entirely new GUI from scratch, but anyone wanting to build any front-end or application using Mupen64Plus is welcome.  The 2.0 API is fully documented at: [http://mupen64plus.emuwiki.com]("http://www.emuwiki.com/index.php?title=Mupen64Plus_v2.0_Core_API_v1.0"). The Console front-end is also quite simple and provides an excellent reference for understanding the operation of the new modular architecture.  All of our Win32 users would undoubtedly be eternally grateful if someone created a native Win32 GUI for them.  This could even be done in C#.
[*] Joystick configurations
We have added a new auto-configuration feature to the SDL Input plugin which will automatically setup the joystick configuration for any joystick which is recognized.  If you have a joystick which is not recognized yet, please follow the instructions in this [emutalk post]("http://www.emutalk.net/showthread.php?t=49731") so that we can add support for your controller.
[*] Windows developers
All of the packages in the Mupen64Plus source code bundle will now build directly in Visual Studio 8 (2005) and 9 (2008); the  build instructions are in [this]("http://www.emutalk.net/showthread.php?t=50200") thread.  Windows C/C++ developers are encouraged to get involved.  Currently there is no Win32 installer for Mupen64Plus.  It would be very helpful if someone could set up a installer project to create an installer.
[/LIST]

To download Mupen64Plus v1.99.3, just grab the package that you want:

[mupen64plus-bundle-linux32-1.99.3.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-linux32-1.99.3.tar.gz")
[mupen64plus-bundle-linux64-1.99.3.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-linux64-1.99.3.tar.gz")
[mupen64plus-bundle-win32-1.99.3.zip]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-win32-1.99.3.zip")
[mupen64plus-bundle-src-1.99.3.tar.gz]("http://mupen64plus.googlecode.com/files/mupen64plus-bundle-src-1.99.3.tar.gz")

OSX: coming soon

The MD5 sums for these packages are:

fd2114c5fc5548c92d5dd35ff61be0e6  mupen64plus-bundle-linux32-1.99.3.tar.gz
ef293c3f17aea7ae404609c24b111040  mupen64plus-bundle-linux64-1.99.3.tar.gz
cc3cb29ac082649f8d197c3f9e3ca9d5  mupen64plus-bundle-src-1.99.3.tar.gz
f01deb5f3e1766c5f140260652ad9dd3  mupen64plus-bundle-win32-1.99.3.zip

Mupen64Plus has a [Home Page]("http://code.google.com/p/mupen64plus/") over at Google Code, with lots of useful information, screenshots, a bug tracker, a discussion forum, etc.  The new Mupen64Plus API is documented at [http://mupen64plus.emuwiki.com/]("http://mupen64plus.emuwiki.com/").

---

### Post by hikaricore on 2010-02-15
Sweet.

---

### Post by rflores2323 on 2010-03-01
will this be updated in the ubuntu karmic software center??? currently I think only the 1.5 is in there.  Would be nice to have it in there for the newbies like myself to install it easily.

---

