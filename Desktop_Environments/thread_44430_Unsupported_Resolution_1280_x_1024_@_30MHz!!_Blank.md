---
title: "Unsupported Resolution 1280 x 1024 @ 30MHz!! Blank Screen"
date: 2005-06-26
forum: Desktop Environments
---

### Post by podrik0 on 2005-06-26
Help,
New to linux
Just installed everything correctly, rebooted, then at log in, it set my resolution to 1280 x 1024 @ 30MHz

I need at least 60MHz for my DVI TFT to support this as it is picky!

I can't get into the OS at all yet, well I have typed my user + pass without seeing a thing and think I logged in blind as I heard some music lol?

How do I change it from recovery mode? As I know can type things via the root thing

I will need precise words to type as I know nothing at the moment but pick up on things easily usaully 

Thank You  O:)

---

### Post by Paulus on 2005-06-26
dont' worry my friend; i have been in this position many times!  It's a shame DVI isn't supported as much as it is in windowz
Can you tell us exakly what you did to end up in this posision.  Did you edit your xorg.conf file to get the resolution?

if so, from your command point just type [PHP]sudo nano /etc/X11/xorg.conf[/PHP] then you can hopefully undo whatever you did!

just for reference, this is the only way i can get 1280 i have to add 1280x1024 to Section "Screen" to get the resolution, then where the Section "Monitor" is, I have to add simply a "1" infront of the last frequencys (on both lines) make sense? no?  well this is mine:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-149
	VertRefresh	43-172

---

### Post by podrik0 on 2005-06-26
I did nothing  O:) 

I left it installing and fell asleep, then woke up to find the out of reach error on my display evn with restarts same thing.

Gonna try your tweak now will let you know how it goes  ;-)

---

### Post by Paulus on 2005-06-26
ok, well if you did nothing (which i assumed you didn't do) what i told you to do will basically edit your graphics card and monitor configuration file...  try and find the sections i mentioned above, this is the sections you have to change, 

**Section "Screen"**- add (if not there) 1280 to the last part of that section.  E.G:
SubSection "Display"
		Depth		24
		Modes		**"1280x1024" **"1024x768" "800x600" "640x480"

**Section "Monitor"**- this is most probably where your problem lies (wrong spelling?)  do what i said above, this is how mine reads:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	27-[COLOR=DarkOrange]1[/COLOR]49
	VertRefresh	43-[COLOR=DarkRed]1[/COLOR]72
EndSection
make sure those 1's are there!

Hope this makes sense, try not to get too scared of the commmand prompt stuff!

---

### Post by podrik0 on 2005-06-26
:grin: 
Well I been there and ran off lol
I saw the parts, well I don't know how to save it and exit etc?

I see you have things like ^M etc
I don't know how to perform these via a keyboard!
Any idea
Thanks again

---

### Post by Paulus on 2005-06-26
don't worry. i had the same problem!   The only way i worked out how to save it to press **alt-x** thats what the ^'s mean, they mean alt!

---

### Post by podrik0 on 2005-06-26
Thanks on my way now  O:)

---

### Post by podrik0 on 2005-06-26
Thanks!
 HorizSync 27-149
VertRefresh 43-172

They was both missing for some reason!!

Now the screen doens't go off at log in

However after typing in the log in, it just says You have new mail or something like that

Staying at the command thing?

Why isn't it loading the desktop  ](*,) 

Really want to get this working but tripping over one thing or another lol

Thanks in Advance

---

### Post by Paulus on 2005-06-26
hmmm, amazing problems for your first install.   To load the gui, you type "startx" after you've logged in.   It should be all nice and Gui, i suspect it might come up some errors when you type this, post em here!

btw it always says you got mail, I can't find this mystery mail!

---

### Post by podrik0 on 2005-06-26
:grin: lol!

I think I'm gonna re-install it, so many problems!
I installed it last night about 3AM so more than likely missed something vital!

I will be back on posting on the results or more problems! in about 3-4 hours from now!

Gonna go get some breakfast!

Thanks for your help so far  :)

---

### Post by Paulus on 2005-06-26
no probs!  I was just going to suggest a reinstall!
Good luck

Paul

---

### Post by podrik0 on 2005-06-26
Great - Same problem

Edited Conf again added same Horizsync & Vert etc again

Same problem!

Locks onto 30MHz Referesh!! :neutral: 

It recognizes my graphics card and tft model and manufacturer 100% correctly so I don't see whats happening

Any ideas?

---

### Post by podrik0 on 2005-06-26
I get the following message everytime no matter what

"temporary failure in name resolution" FAIL

No idea if this will help fix my display!

---

### Post by godzero on 2005-06-26
If you were to login (in tty/shell/cli) and then type "mail" it'll list the mail it sent you.

There should be a clue or two in there.

What vidoe card are you using?

[EDIT]

yes, that helps. Your X windows session communicates with the OS via TCP/IP, using your system's network name (usually localhost, but in your case.. prolly something else)

The computer's name is in /etc/hostname

---

### Post by podrik0 on 2005-06-26
Pentium 4
ASUS Pundit-R
ATI Radeon 9100 IGP
Seagate 80GB
HDA Digital X-Mistique 7.1
Xerox 17" @ DVI

---

### Post by podrik0 on 2005-06-26
Anyone have any ideas before I give in to my attempts to convert to linux?  :???:

---

### Post by godzero on 2005-06-26
[QUOTE=podrik0]Anyone have any ideas before I give in to my attempts to convert to linux?  :???:[/QUOTE]
 "temporary failure in name resolution" FAIL

makes me think your hostname is something like "mycomputer.mydomain", or has illegal charaters in it.

---

### Post by podrik0 on 2005-06-26
SORTED

Switched from DVI to VGA

Thankfully have both outputs off my TFT

So was on VGA had the same out of reach error but at 85MHz

So then adjusted VertRefresh to 43-75

Then got into it perfect!

---

### Post by Takis on 2005-06-26
[QUOTE=Paulus]btw it always says you got mail, I can't find this mystery mail![/QUOTE]
This tends to be a different sort of mail, it's (comparatively) not used that much these days for human to human conversation. If you open a shell, type 'mail' and it'll come up. They tend to be system messages. A very quick run-down on how to use it:
(h)eaders: print a list of headers (i.e. show you all the messages)
(t <number>): 'type' (print) a message, designated by number.
(d <number>): delete a message, designated by number.
(q): quit, saving changes
(e): exit, not saving changes

NB you can also type (e.g.) 'd 1-5' which deletes messages 1 through 5.

For proper information, type 'man mail' at the prompt.

---

