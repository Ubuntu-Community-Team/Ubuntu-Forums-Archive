---
title: "How do you save games in psX emulator?"
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by TWO on 2008-01-01
Does anyone now how to save games on the psX emulator. I have created a folder and assigned it as one of the memory cards for the program. 

Each time I play a game, the 'card' is recognised however I am first asked to format it then save. On quitting the program then going to load, there is no save file there.

Is there something that I am missing or have I just set it up incorrectly.

Thanks in advance!

TWO

---

### Post by acoustibop on 2008-01-01
Most games will format cards automatically, TWO, but some won't.  However, it's easy to do: just load the card(s) and, instead of starting a game, let the emulator run to the BIOS pages - you'll need to have your controller Type set as 'SCPH-1010: Normal pad' for this - and select the memory card editor.  When pSX opens the editor, it will format the card(s) - exit the editor, and that's all you need to do.

This is referenced in the [FAQ on the official pSX forum]("http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1153769834#1153770101").

---

### Post by dfreer on 2008-01-01
> **TWO said:**
> On quitting the program then going to load, there is no save file there.

Sounds to me like pSX can't save the card file, possibly due to incorrect permissions (like pSX can't write to the folder where you are trying to save your card).

---

### Post by acoustibop on 2008-01-01
Well, first things first, dfreer - it's quite possible that the reason is as I outlined, and that's the easiest one to check.  pSX now puts memory cards, quick saves etc in ~/.pSX by default, so hopefully that should obviate permissions problems.

FWIW I always format new memory cards in the editor anyway - better safe than sorry!

@TWO: what game(s) are you having this problem with - and how did you create your memory card(s)?

---

### Post by TWO on 2008-01-02
> **acoustibop said:**
> @TWO: what game(s) are you having this problem with - and how did you create your memory card(s)?

I'm currently playing Final Fantasy VII.
Truth be known, I assumed that all there was to it was to assign a folder as the memory card in the frontend menu. Is there something else that I need to download for the program to treat the file as a memory card?

This is the first emulator that I've used so I'm not quite sure what to expect...

---

### Post by acoustibop on 2008-01-02
No, you need to create memory cards in your selected folder, TWO.  Go to File -> Configuration -> Memory cards and type the names of the cards you want to create in slots  1 & 2.  Then click OK.  This will create the cards; then it's best, as I said before, to open them in the memory card editor to format them.

You can create as many memory cards as you like.  I generally create two for each game I'm playing, and put them in a subfolder for each game - keeps things tidy.

You can use [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") to set the appropriate cards, as well as pretty much all the settings you might want to change on a per game basis, for each game you play.

---

### Post by b4d on 2008-01-02
try with f6, f7, f8, then you can load game by pressing f1, f2, f3

---

### Post by acoustibop on 2008-01-02
That's quick saving, or save states, not memory card saving, b4d, and it's a bad idea to depend on them.

Emulating a game tends to produce errors over time.  Normally, when you save your game to a memory card, this will strip away any errors, because a memory card save is not a 'snapshot' of the game, it's just a record of the parameters of the game at that point.  Reloading a game from a memory card save is like starting the game anew, but with a set set of parameters that puts you back in the game at the point where you saved.

A save state (or quick save), however, is a 'snapshot' of the game at that point, and includes any errors that may have occurred.  So when you reload the save state, you reload the errors, and they will continue to accumulate until the game becomes unplayable.  This, apparently will also happen on a console, but you'd usually have to have a pretty mammoth playing session to see it, as there are no save states - in order to save, you have to save to a memory card,

The solution to this in an emulator should be to save to a memory card, which should remove the errors - but, unfortunately, it seems that one of the first things to be affected by the accumulation of errors is saving.  So, by the time your game starts becoming unstable enough to notice, it's often well past the point where you can save any more.

It's fine to use save states during a game session, but I'd say it's a good idea always to end the session with a memory card save, and to start the next session by reloading from that save.

---

### Post by TWO on 2008-01-03
> **acoustibop said:**
> No, you need to create memory cards in your selected folder, TWO.  Go to File -> Configuration -> Memory cards and type the names of the cards you want to create in slots  1 & 2.  Then click OK.  This will create the cards; then it's best, as I said before, to open them in the memory card editor to format them.

You can create as many memory cards as you like.  I generally create two for each game I'm playing, and put them in a subfolder for each game - keeps things tidy.

You can use [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") to set the appropriate cards, as well as pretty much all the settings you might want to change on a per game basis, for each game you play.

OK. I have name one of the memory card slots. Should something now appear in the folder allocated for memory cards because it hasn't. Also, where is the option for formatting the memory card (?) because I don't see any.

I already had the frontend that you mentioned.

Thanks in advance
TWO

---

### Post by acoustibop on 2008-01-03
If you typed a name in the memory card slot and clicked OK and OK, that should have created a card, TWO.  If it hasn't, it suggests you have permission problems, as dfreer suggested.  Have you checked the permissions on your pSX folder?  And where is the folder - how did you install pSX?

Formatting the card is easy, but (obviously) won't work if you don't have a memory card.  Just set the card in a slot and, instead of starting a game, just let the emulator run to the BIOS screen - that's the one that shows the options of the memory card editor and the CD player.  Select the memory card editor, then, after it opens, close it again.  That will format the card.  Don't forget you have to have your controller Type set to 'SCPH-1010: Normal pad,' or you won't get a cursor on the BIOS screen and so won't be able to open the editor.

---

### Post by TWO on 2008-01-03
Ah, I see. Well I have reassigned the folder paths to the original ones. I had them linked to folders that I had created on my shared partition, as I was thinking of running another emulator in a different OS. 

Saved state seemed to be able to write correctly to the shared partition but the same couldn't be said of the memory cards.

The pSX folder is in my home directory and was installed either via the Terminal or the add/remove applications GUI. (I can't remember which, but I am certain that I didn't install it from a .deb file.)

It seems that somehow I have created a new problem in that the psX frontend is now refusing to start. All I did was change the paths of the save state and the memory card to the default paths of pSX. The program then began complaining that I hadn't selected a BIOS which I had done already.

In the terminal, the following appeared:

> :~$ psxfrontend
Traceback (most recent call last):
  File "<string>", line 478, in <module>
  File "/usr/lib/python2.5/ihooks.py", line 404, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.5/ihooks.py", line 440, in find_head_package
    q = self.import_it(head, qname, parent)
  File "/usr/lib/python2.5/ihooks.py", line 495, in import_it
    m = self.loader.load_module(fqname, stuff)
  File "<package>", line 28, in load_module
  File "frontend.py", line 1, in <module>
  File "/usr/lib/python2.5/ihooks.py", line 404, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.5/ihooks.py", line 440, in find_head_package
    q = self.import_it(head, qname, parent)
  File "/usr/lib/python2.5/ihooks.py", line 495, in import_it
    m = self.loader.load_module(fqname, stuff)
  File "<package>", line 28, in load_module
  File "globals.py", line 67, in <module>
  File "configobj.py", line 630, in __init__
configobj.ConfigObjError: Parsing failed with several errors.
First error at line 18.
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "<string>", line 478, in <module>
  File "/usr/lib/python2.5/ihooks.py", line 404, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.5/ihooks.py", line 440, in find_head_package
    q = self.import_it(head, qname, parent)
  File "/usr/lib/python2.5/ihooks.py", line 495, in import_it
    m = self.loader.load_module(fqname, stuff)
  File "<package>", line 28, in load_module
  File "frontend.py", line 1, in <module>
  File "/usr/lib/python2.5/ihooks.py", line 404, in import_module
    q, tail = self.find_head_package(parent, str(name))
  File "/usr/lib/python2.5/ihooks.py", line 440, in find_head_package
    q = self.import_it(head, qname, parent)
  File "/usr/lib/python2.5/ihooks.py", line 495, in import_it
    m = self.loader.load_module(fqname, stuff)
  File "<package>", line 28, in load_module
  File "globals.py", line 67, in <module>
  File "configobj.py", line 630, in __init__
configobj.ConfigObjError: Parsing failed with several errors.
First error at line 18.


That's rather annoying. Just to check,  I entered 'psx' into the terminal and it too has developed problems... :(

> BIOS not found
This emulator requires a BIOS image which must be installed in the bios folder.

I'm not too sure what has gone on in the last few hours because the program was working fine except the memory card function. 

(It does appear that the emulator runs by selecting it from the menu though....)

Oh dear.

---

### Post by acoustibop on 2008-01-03
pSX is not difficult or time-consuming to configure, TWO, so your best bet is to delete your psx.ini (configuration file) which should be in ~/.pSX.  When you restart pSX, it'll create a new psx.ini and you'll be starting over again.  Do the same for pSX Frontend - it also puts its configuration file, psxfrontend.ini, in ~/.pSX.  Make sure you've configured pSX before you run the Frontend.

If your configuration files aren't in your ~/.pSX folder, they'll be in your pSX folder.  If you delete these, pSX will recreate them in ~/.pSX.  Since your pSX folder is in your Home folder, you've probably installed it the same way most people do, simply by extracting it from the .tar.bz2 file.  It's a good idea to make sure you use the right switches for this, so you preserve the correct file permissions: I usually put the .tar.bz2 package in my Home folder and do "tar xvpf <pSX_package.tar.bz2>"

FWIW I also put my BIOS file, image, memory card and save state folders on a shared partition - it's actually an NTFS partition - so I can share them between 2 Ubuntu installations and a Windows (almost defunct now) one.  I do the same on another machine with a FAT32 partition.  Both work fine for me, but with shared partitions, you do need to make sure permissions are set properly.  There's no inherent problem with doing this in pSX; if it's not working, there's some other reason.

---

### Post by TWO on 2008-01-05
> **acoustibop said:**
> pSX is not difficult or time-consuming to configure, TWO, so your best bet is to delete your psx.ini (configuration file) which should be in ~/.pSX.  When you restart pSX, it'll create a new psx.ini and you'll be starting over again.  Do the same for pSX Frontend - it also puts its configuration file, psxfrontend.ini, in ~/.pSX.  Make sure you've configured pSX before you run the Frontend. 
 Having not really used emulators before, I would be quite unaware as to how difficult or not things might or might not be to configure.

> 
FWIW I also put my BIOS file, image, memory card and save state folders on a shared partition - it's actually an NTFS partition - so I can share them between 2 Ubuntu installations and a Windows (almost defunct now) one.  I do the same on another machine with a FAT32 partition.  Both work fine for me, but with shared partitions, you do need to make sure permissions are set properly.  There's no inherent problem with doing this in pSX; if it's not working, there's some other reason.

OK, well I seem to have had more success with setting up the memory cards this time (having deleted the .ini files), thanks to your advice. A file type of some sort has appeared in the file that I've allocated for memory cards. Furthermore, this is on my shared partition as well so that too is a bonus. I'm currently playing the game again as I type this so I will soon test whether the game can be successfully saved on the memory cards that I've created. 

I will confirm this very shortly. :)

Whilst on the topic of emulators, I wonder if I could ask you what I should have   as the correct Latency/ XA Latency settings under the sound menu? I have increased the value enough to stop the annoying jumping of the sound however I occasionally hear a 'static' sound at random points during game play.

Many Thanks

TWO

---

### Post by TWO on 2008-01-05
I can confirm that the memory card setup works successfully. Thanks very much. :)

TWO

---

### Post by TWO on 2008-01-05
Out of curiousity, can other emulators use the save states of pSX?

---

### Post by acoustibop on 2008-01-05
No, save states are usually emulator specific, TWO - in fact, save states from different versions of the same emulator won't always work.  The memory cards from almost all emulators are portable, however, and it doesn't even matter that much what extension they have.  Emulators like ePSXe will look for a specific extension (.mcr) but will open an appropriate memory card with any extension (or no extension) quite happily if you type the name in.

Latency settings are whatever works for you.  It's best not to increase latency more than necessary, as it's essentially a delay and, if you increase it too much, the sound may go out of sync with the game.  If you find yourself having to increase it a lot, this suggests your system has very high latency - this may be because of a poor soundcard, or may be because you've modified the kernel - vanilla Gutsy seems to have got the latency down far enough that pSX will run without latency increase on a good soundcard.

FWIW I'm running two installations of Gutsy on this machine: on one I installed the current 7.12 fglrx driver, and on the other I installed the 8.37.6 driver that's in the repositories, through the Restricted Drivers Manager - I'm using an ATI card, of course.  The reason for this was that I found installing the 7.12 driver does increase sound latency on the system - not a lot, but enough that I have to increase the latency values for pSX.  This may be, I think, because of the changes to the kernel.  On the installation with the 8.37.6 driver, however, latency is sufficiently low that I can run pSX with no alteration to the latency settings, and I find some other games, which also seem to be more affected by latency values than videocard speed, run better on this installation too.

**Edit:** a few more points on reading/writing/creating memory cards on a separate partition: it's probably a good idea to make sure there are no spaces in the paths to your memory cards; Gutsy should handle spaces fine, but better safe than sorry.  It may be a good idea to try to keep the paths entirely lower case as well if your memory cards are on a Windows partition: Windows doesn't distinguish between upper and lower case in paths, while Linux does; therefore, it's possible your Windows installation may mess things up.

Did pSX Frontend also run Ok after you deleted its .ini file?  It looked from you previous post that there might be a Python problem: quote from Ultima in the [development thread]("http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=1155421460#1174026819"):
> Dependencies that I can think of off the top of my head:
- Python (might need 2.4 or higher)
- PyGTK (2.8 or higher, I believe)
- zlib (not 100% sure about this one)

Might be an idea to check you have those installed.

---

### Post by dragoonwisper on 2009-03-01
I have a question..how do you delete saved games though? like lets say a final fantasyy 7 saved game, how?

---

### Post by dfreer on 2009-03-01
> **dragoonwisper said:**
> I have a question..how do you delete saved games though? like lets say a final fantasyy 7 saved game, how?

If I understand your question correctly, just boot pSX without a CD image/game in the drive. It will load the BIOS and you can manage your memory cards from there, including copying/deleting saved games.

Some games also allow you to manage their specific saved games from the main menu screen, allowing you to delete just the saves for that game.

---

