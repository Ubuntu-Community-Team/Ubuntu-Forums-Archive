---
title: "How to Launch Games In Cedega?"
date: 2005-05-22
forum: Gaming &amp; Leisure
---

### Post by malachakla on 2005-05-22
Hi,
I've installed Cedega, and installed a windows game.
Now, this is going to sound REALLY stupid, but how do you run the game?
The windows application for the game is in a folder called "Program Files" with a space in between program and files, and when i try to run the game using the terminal the terminal thinks that the space between program and files means another command.

How do I open a game?
Do I have to rename the Program Files folder?
Thanks very much for patience.

---

### Post by bored2k on 2005-05-22
[QUOTE=malachakla]Hi,
I've installed Cedega, and installed a windows game.
Now, this is going to sound REALLY stupid, but how do you run the game?
The windows application for the game is in a folder called "Program Files" with a space in between program and files, and when i try to run the game using the terminal the terminal thinks that the space between program and files means another command.

How do I open a game?
Do I have to rename the Program Files folder?
Thanks very much for patience.[/QUOTE]
 cedega "Program Files\Steam\Steam.EXE"

---

### Post by malachakla on 2005-05-22
So the quote marks make the difference?
What happens when I enter the path with the quote marks is:

root@mantra:~# cedega "/home/jonathan/TransGaming_Drive/Program Files/EA GAMES/Battlefield Vietnam/bfvietnam.exe"
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
cmd:

and then nothing happens and it goes back to my prompt.

---

### Post by pdk001 on 2005-05-23
[QUOTE=malachakla]Hi,
I've installed Cedega, and installed a windows game.
Now, this is going to sound REALLY stupid, but how do you run the game?
The windows application for the game is in a folder called "Program Files" with a space in between program and files, and when i try to run the game using the terminal the terminal thinks that the space between program and files means another command.

How do I open a game?
Do I have to rename the Program Files folder?
Thanks very much for patience.[/QUOTE]
here is the tip for you [http://www.ubuntuforums.org/showthread.php?p=183156#post183156](http://www.ubuntuforums.org/showthread.php?p=183156#post183156)
i had a same problem though just solved it

---

### Post by malachakla on 2005-05-23
Grazie, I'll try it i tonight.

---

### Post by malachakla on 2005-05-23
Itworksitworksitworks!!!!
Yay!
It's so nice to have something working properly in Ubuntu... I've had such troubles with other stuff...
Thanks for all the help, I'm off to play GTA  \\:D/

---

### Post by JohnC86 on 2005-05-30
I'm having some problems getting this game to work, this is the error from terminal:

Jonneh$ cedega Grand\ Theft\ Auto.exe
/usr/bin/cedega: line 348: 13071 Segmentation fault      $SHELL -c "$RUNWINE $WINVER -debugmsg $DEBUGMSG -use-dos-cwd $WORKDIR $EJECT $DT -- $COMMAND_LINE"

I haven't got a clue what to do now lol

I tried in Wine too, but got this error:

Invoking /usr/lib/wine/wine.bin Grand Theft Auto.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Wine exited with a successful status
/usr/bin/wine: line 609: 13133 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

        This dialog box is a temporary status dialog to let you know
        that Wine is attempting to launch your application.

        Since Wine is still very much in a development stage,
        many applications will fail silently.
        This dialog box is your indication
        that we're *trying* to run your application.

        This dialog box will automatically disappear after 30 seconds,
        or after your application finishes.

        You can permanently disable this dialog by selecting
        the option below.
        " 2>/dev/null

Of course i didnt want it to exit, it just exited successfully on it's own.

Any idea's? Google isn't much help :(

---

### Post by dmn_clown on 2005-05-30
> Any idea's? Google isn't much help

The full version of the game appears to be untested according to the unofficial  [TransGaming wiki](http://digital-conquest.ath.cx/wiki/index.php/Grand_Theft_Auto) try asking in the [TransGaming Forum](http://transgaming.org/forum/) maybe someone there has gotten it working.

---

