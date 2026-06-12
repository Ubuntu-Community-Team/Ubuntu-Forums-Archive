---
title: "Where is the wine.config file?"
date: 2006-08-26
forum: Gaming &amp; Leisure
---

### Post by Mcavity on 2006-08-26
I have installed a program that I need to run via wine, and it seems to work ok, however there is no text in the application. Its not displaying the fonts.
I Did some digging around and found that I need to change a setting in the ~/.wine/config. however when I go there.. there's is no config. file.
The next bit of info I tracked down is that there's supposed to be a demo copy of the file in dir_to_wine_source_code/documentation/samples/config
however I cant find that either..

This is what I need to set. 

; Use the Render extension to render client side fonts (default "Y")
"ClientSideWithRender" = "N"
; Fallback on X core requests to render client side fonts (default "Y")
"ClientSideWithCore" = "N"
; Set both of the previous two to "N" in order to force X11 server side fonts

Can anyone help?

---

### Post by DoktorSeven on 2006-08-26
It's all done by "registry" (actually a text file in a registry-like format, but easier to access through regedit like windows does) now, the config file is depreciated.

This is just a guess, but from a search it looks like it needs to be under Software\Wine\X11 Driver.  So try running **regedit** and go to HKEY_CURRENT_USER\Software\Wine\X11 Driver (or maybe HKEY_LOCAL_MACHINE, but I didn't see an "X11 Driver" part under Software\Wine) and add those values (new->string value).

---

### Post by Mcavity on 2006-08-26
Ok so its configurable via a regestry now. Good to know. however..
I cant find HKEY_CURRENT_USER\Software\Wine\X11 Driver 

also doing some digging it looks like this is basicly the same as turning "FreeType=N"
But I cant for the life of me figure where I would put this.
Any Ideas? 

[semi clueless user]

---

### Post by Mcavity on 2006-09-06
Hey anyone figure this out? I realy could use an answer...

---

### Post by DoktorSeven on 2006-09-06
No idea.  For keys that don't exist you can just create them in regedit (the X11 Driver part).  Not sure where you would put that FreeType="N", though; did you get that from something you would have put in wine.config?  

Usually there is a path in a line above a given key->value for wine.config (like the Software\Wine\X11 Driver path for the first set of keys) that you would just translate into the same path in regedit either under HKEY_LOCAL_MACHINE or HKEY_CURRENT_USER.  Create that path in regedit then add the key->value under it.

---

### Post by Mcavity on 2006-09-07
yes thats exactly what I would need to drop into wine config.

The game is magic online. Its a free download and you dont need an account to try it out. I pont this out just incase anyone wants to help figure out how to get this working. 
I did get it working a few years ago but that wis with the old config.

---

### Post by theintuit on 2007-02-22
Well im having a bit of an issue too with Wineconfig Im running DVD decrypter on wine and it doesnt notice any drives I mount a DVD in linux and BAM nothing just sits there.
Another thing is that Wine never came up with a GUI config after i instaled the package And it always gives me error 44 msgs in terminal.... Ima ata a loss 

ive been trying to put this :      CFLAGS=-fno-stack-protector ./configure    into the config file i thaught that might help with the crashes and stuff but im lost...HELP

---

### Post by ChesterBr on 2007-05-14
It took a while, but I FINALLY managed to solve this issue.

As the original poster, I needed to enable those settings. In my case, I am using NXFree to log into a remote Gnome session on an Ubuntu machine, and using Wine on it - it's because my main computer is a pre-Intel Macintosh (and thus cannot run Wine).

**Techinical stuff** (you can skip it and go straight to the solution below)

A big difference between Windows and UNIXes is that, while UNIX applications save their settings in config files, Windows apps generally save them in the registry, a sort of database for settings.

Wine is a unix app, so it used to store its settings in wine.conf or ~/.wine/config, but since it has to emulate the registry anyway (for Windows apps that demand it), they seem to have decided to store their own settings in their simulated registry - so the file we are looking for doesn't exist anymore. Grrrr!

For that reason, the settings must be introduced into the registry. The safe way to do so is to use regedit (a clone of the Windows software that allows you to edit the registry).

Unfortunately, it does not display its fonts (just as winecfg and the apps you wish to run). But there is a solution: we can describe the settings in a temporary file and politely ask regedit to input them into Wine's simulated registry.

[B]
Solution in three steps:[/B]

1) Create a "settings.txt" file with your favorite text editor (vi, emacs or the Gnome Text Editor under Acessories) with the following three lines:
[INDENT][FONT="Courier New"][HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"
"ClientSideWithCore"="N"[/FONT][/INDENT]
(there should be no extra spaces - for example, a space before or after the equal (=) symbol will cause you trouble).
b) Execute the following command:
[INDENT][FONT="Courier New"]regedit settings.txt[/FONT][/INDENT]
c) Run a wine app, for example:
[INDENT][FONT="Courier New"]winecfg[/FONT][/INDENT]

It will take a while and display several messages, but, in the end, it will fix the "invisible fonts" problem (the one that makes most people want to turn off client-side rendering). 

You can now use regedit (without parameters) to add/remove/change settings (navigate to the key path on the first line of step 1). If regedit does not work anymore, you can repeat the procedure changing "N" to "Y", or even try editing the settings out from ~/.wine/user.reg (at your own risk, I just noticed the settings are appended there, with some magic number on the key name).

Good Luck,
  Chester

---

### Post by ChesterBr on 2007-05-14
Aargh, 1, b, c should read 1,2,3... sorry, late night posting! :-\"

---

### Post by AndrewRiedi on 2007-05-14
> **ChesterBr said:**
> Aargh, 1, b, c should read 1,2,3... sorry, late night posting! :-\"

Ever hear of the edit button?  :wink:

---

### Post by Farmer of Bricks on 2009-03-31
Thank you, ChesterBR. Now I can run West Point Bridge Design 2007.

---

