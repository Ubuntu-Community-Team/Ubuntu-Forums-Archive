---
title: "Zenity - What am I doing wrong?"
date: 2005-12-17
forum: Desktop Environments
---

### Post by starNIX on 2005-12-17
I am trying to write a script that will rip a dvd and display a zenity progress dialog.  Well,  it displays the dialog but the progress bar doesn't do anything.

Anyone know whats wrong?

#!/bin/bash
# needs to be bash for the redirection to work.
dvdbackup -M -i /dev/hdc -o /home/bpregont/Documents/dvd_rips \
 | zenity --progress  --pulsate --text "Ripping DVD - Please wait..." 
done

---

