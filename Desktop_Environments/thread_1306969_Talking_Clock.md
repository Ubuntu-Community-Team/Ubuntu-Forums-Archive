---
title: "Talking Clock"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Rodney9 on 2009-10-30
> echo "Its" `date "+%l oclock"` | aoss festival --tts

does not work in Gnome-Schedule because it says the percentage symbol is unusable by cron.

Is there a better 'Talking Clock' for Karmic Koala 9.10 64Bit

I need to hear the time each half hour.

Thanks.
Rodney

---

### Post by Rodney9 on 2009-10-30
So use a text editor (Accessories -> Text Editor) to create a file called speak_time in your home directory with the following lines;

#!/bin/sh
echo "Its" `date "+%l oclock"` | aoss festival --tts

Next you have to allow the text file to be executable, so type this command into the terminal;

chmod +x ~/speak_time

Then you can put the script name as the command in your scheduled task;

~/speak_time

Note the use of ~ (shorthand for you home directory) to give the path to the script.

Also, %l in the date format gives the hour. You mentioned every half hour so you will be hearing "10 oclock" even on the half hour. Use %l %M to gets the minutes in there.

Edit:  for use of gnome-schedule.

---

