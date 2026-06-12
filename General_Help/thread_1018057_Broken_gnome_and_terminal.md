---
title: "Broken gnome and terminal"
date: 2008-12-21
forum: General Help
---

### Post by BlackCat13 on 2008-12-21
Hey everyone...

Some help is needed if possible...

My computer is an Asus X52S laptop with Core2 Duo and the N-Vidia 8600M GS... running Hardy Heron (8.04) with some other packages from Ubuntu Studio and some custom installs. Using gnome (obviously= Ubuntu) with Compiz and Emerald. The installation worked straight out of the box for most things... including wireless internet... has been really stable and handles most everything I throw at it. Because of the Audio work that I do (Ardour) it is running on the RT Kernel.

I also run Wine and game with WoW... Having installed the new WoW expansion WoTLK I had two annoying glitches occur... an echo (stuttering) in the audio and an issue with the mouse losing its ability to interact with various in-game windows from time to time... my efforts to find a solution to these issues drew a blank... it appeared from my googling and questions that I alone was suffering from these... I was sort of OK for the moment with the audio... it wasn't too inconvenient however the Graphics issue is a major pain causing me to have to crash the application (Alt + F4) and restart every time it glitched... and it would glitch roughly every 5-10 minutes.

So... I tried updating my Graphics driver to the 180 release in the Jaunty package... a long story short... it didn't work... no real surprise... I managed to revert to the old 169Rev driver with no problems :) HOWEVER it still hadn't handled the problem so I attempted to upgrade to Intrepid on the reasoning that I could at least get to the 177Rev driver... unfortunately all attempts at upgrade failed... I "guess" because parts of the jaunty package were still lurking (when I first tried the 180Rev install a boatload of changes were made by synaptic... including Gnome Desktop... and I started to get errors at boot of the unable to access - connection refused kind :( 

SO (panicking a bit now) I "thought" of trying to go through and remove gnome-terminal-whatever (brain explosion yes I know) using Synaptic and reinstall teh earlier version in the same way that I had "undone" the Graphics driver issue... bottom line it went... along with Nautilus :( and NOW I cannot browse or open folders.  Error message of "Could not open location 'file:///home/... There is no default action associated with this location.  :(

No problems, thinks I, let's open the terminal and have a look... (Error: "Could not launch menu item... Failed to execute child process "gnome-terminal" (No such file or directory)" :(

OK Right-Click Desktop -> Open Terminal = ... waiting... waiting... still waiting... nothing :( :(

SO... I have STOPPED trying to fix it... which is the first sensible thing I did tonight... and I am posting this in the hope that someone somewhere can guide me in the direction of recovering my system...

UPDATE: Things got worse... I was able to log into the terminal using <CTRL> <F2>... which was good however I was unable then to apt-get install gnome-terminal... because it came back with missing dependency gnome-control-center... so added that... which came back with a list of libraries... libvte9 libgtk2.0-0 libglade2-0 libxi6... etc all with a version number in brackets after it eg libvte9 (>= 1:0.16.9) which are needed...

So I tried to install the libraries first but it comes back that the latest versions are already installed... so then I tried to uninstall them so that I could reinstall them but that was going to uninstall a zillion packages with it so I aborted that (it is how I got into this trouble) I also tried "apt-get install --include dependencies" but the syntax is wrong...

The after a reboot I lost the bility to log in graphically at all... so I am now operating for the moment of a fresh partition and Linux Mint... (pretty good distro btw) anyway

Cheers
Greg

---

