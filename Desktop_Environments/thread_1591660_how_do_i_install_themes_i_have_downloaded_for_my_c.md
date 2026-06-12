---
title: "how do i install themes i have downloaded for my conky?!"
date: 2010-10-09
forum: Desktop Environments
---

### Post by baraka607 on 2010-10-09
hi all, please am having this problem of changing the looking of my conky. so help me how to install the themes for conky i have downloaded.
thank you alot and waiting for your reply.

---

### Post by Frogs Hair on 2010-10-09
If your themes came with read me or index files check them for instructions.

---

### Post by baraka607 on 2010-10-10
i managed to find the read me text but i don't know what's next...?!
what should i do next?!


### Install ###
Copy the fonts to your font dir (~/.fonts).
Copy the Scripts to "~/scripts".
Copy the Mira_* folders to "~/.conky".


### Mail ###
The Email part uses the gmail script (Google Mail only).
To set it up edit the gmail.pl script and enter your username and password.


### Weather ###
Type [http://xoap.weather.com/search/search?where=](http://xoap.weather.com/search/search?where=)[yourcity] to find your
location id in your browser and then add your location id to "<<<YourLocation>>>"
in .conkyrc_weather.


### Sys ###
For the Arch Update part read the Readme in the "arch-updates" folder.
If you don't want it, delete line 85-87 in the .conkyrc_sys.

The Gpu part works with nvidia cards only.
 
 
### Start ###
To start all Conkys at once just make little script called "conky_start" (for example)
in "/usr/bin/" or "/usr/local/bin/".

It should look like this:

#!/bin/bash
conky -c ~/.conky/Mira_green/.conkyrc_clock &
conky -c ~/.conky/Mira_green/.conkyrc_weather &
conky -c ~/.conky/Mira_green/.conkyrc_sys &
conky -c ~/.conky/Mira_green/.conkyrc_net &
conky -c ~/.conky/Mira_green/.conkyrc_disk &
conky -c ~/.conky/Mira_green/.conkyrc_mpd


### Transparency ###
If you use Compiz, you can make Conky transparent.

Open the CompizConfig and go to: General Options > Opacity Settings > New
Enter "class=Conky" and setup the opacity degree.





i managed to find the read me text but i don't know what's next...?!

---

### Post by roggenschrotbrot on 2010-10-10
if it helps you: "~" is your homedir (/home/<yourloginname>/), so "~/.fonts" translates to "/home/<yourloginname>/.fonts". files and folders whose names begin with a "." are hidden, you toggle display of these file by hitting alt+h.

edit:
> ### Start ###
To start all Conkys at once just make little script called "conky_start" (for example)
in "/usr/bin/" or "/usr/local/bin/".

It should look like this:

#!/bin/bash
conky -c ~/.conky/Mira_green/.conkyrc_clock &
conky -c ~/.conky/Mira_green/.conkyrc_weather &
conky -c ~/.conky/Mira_green/.conkyrc_sys &
conky -c ~/.conky/Mira_green/.conkyrc_net &
conky -c ~/.conky/Mira_green/.conkyrc_disk &
conky -c ~/.conky/Mira_green/.conkyrc_mpd
i'd use ~/bin instead of /usr/bin or /usr/local/bin. to create a script go to the folder, 
1. rightclick->new file
2. rename file to conky_start
3. open the file in gedit and paste the above code, save
4. rightclick the file->properties->rights->tick executeable

---

### Post by baraka607 on 2010-10-10
> **roggenschrotbrot said:**
> if it helps you: "~" is your homedir (/home/<yourloginname>/), so "~/.fonts" translates to "/home/<yourloginname>/.fonts". files and folders whose names begin with a "." are hidden, you toggle display of these file by hitting alt+h.

edit:

i'd use ~/bin instead of /usr/bin or /usr/local/bin. to create a script go to the folder, 
1. rightclick->new file
2. rename file to conky_start
3. open the file in gedit and paste the above code, save
4. rightclick the file->properties->rights->tick executeable
i have already create the directory for conky. but i don't understand do i need to copy all the mira folders or only their scripts which are found inside each mira folder?!

---

### Post by roggenschrotbrot on 2010-10-10
the hole folders, as called in the startup script:
> conky -c **~/.conky/Mira_green/**.conkyrc_clock &

---

### Post by baraka607 on 2010-10-10
> **roggenschrotbrot said:**
> the hole folders, as called in the startup script:
ooooh thank you it's all good....!

---

