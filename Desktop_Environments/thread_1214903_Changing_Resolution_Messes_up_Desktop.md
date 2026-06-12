---
title: "Changing Resolution Messes up Desktop"
date: 2009-07-16
forum: Desktop Environments
---

### Post by Nyken on 2009-07-16
Changed my video resolution last night in Ubuntu 9.04 and when I logged back in a few moments later, my desktop display was completely garbbled, the mouse pointer frozen and stuck in a small black box.

Tried to figure out if it was a system wide problem or just a user setting messed up by creating another admin user from the command line in recovery mode. Everything was fine logging in as that user, of course meaning one the config files in my ~/home directory was messed up.

I backed up the /home directory to that user account and completely removed that user identity completely and utterly and then readded it. Logged in as that user again, it the problem was gone. I didnt restore any of the config files, except for my .muttrc, .fetchmailrc files.

For future referrence, I was wondering what config file(s) need to be replaced with "clean" ones, should this happen again? I experiment a lot to learn Linux, but usually backup first. Didn't know I'd need to backup to change from 1152 to 1024 resolution. Better yet, if I ever want to change resolutions again, would I need to set up xorg.conf to enable me to do it? :confused:

Thanks in advance,

Ubuntu 9.04
IBM NetVista with Intel onboard video

---

