---
title: "low res graphics at start up"
date: 2009-07-22
forum: Desktop Environments
---

### Post by emanresu on 2009-07-22
the login window at the boot screen had a font that was too large to read in the login window. i was still able to login, but when i used R (statistical package), i had a similar font/resolution problem when graphs and charts opened in a graphical window, the resolution settings for the window made unviewable charts and graphs.

all my other graphics and resolutions seem OK.

i sought help on the R help list and got this response:
Quote:
>> According to your setup, the system should believe that you have an
>> ~8 inch screen (800/96) and
>> the default X11 window is 7x7 inches so
>> there _should_ be plenty of room, but some systems try
>> to outsmart
>> the user and use the actual physical dimensions, which could be
>> smaller (higher >DPI). You might want to check with "xdpyinfo" (from
>> the shell).
> from xdpyinfo:
> screen #0:
> dimensions: 1280x800 pixels (289x21 millimeters)
> resolution: 112x968 dots per inch
Ick!
Yes that will do that to you.
You might want to try putting
DisplaySize 339 212
in the Monitor section of xorg.conf
i changed xorg.conf.

now, when i boot up my computer, i go through the following process:

1)Ubuntu splash screen

2)msg window:
> Ubuntu is running in low graphics mode

The following error was encountered. You may need to your configuration to solve this.

(EE)Problem parsing config file
(EE)Error parsing the config file


3)new msg window with radio button options:
> What would you like to do?
Run Ubuntu in low graphics mode
Reconfigue graphics
Troubleshoot the error
Exit to console login

i select Run Ubuntu...

4)"Standby one minute while the display restarts."

5)a console screen that says:
> 
There already appears to be an X server running on display :0. Should another display number be started? Answering no will cause GDM to attempt to start the server on :0 again
Yes NO

i select Yes

6)The specified display number was busy, so the server was started on display :1.

at this point, i have to wait 10 seconds or so. if i click OK right away, it starts the process over at 4. after the 10 seconds, i get the login window with viewable font.

is there a way to keep my resolution settings the way they are and not have to go through this process every time i start up the computer? the settings are the way that i want them, i see everything fine, but the OS wants to argue about it.

---

