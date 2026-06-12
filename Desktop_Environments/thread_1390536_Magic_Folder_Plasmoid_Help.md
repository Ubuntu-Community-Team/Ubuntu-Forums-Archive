---
title: "Magic Folder Plasmoid Help"
date: 2010-01-25
forum: Desktop Environments
---

### Post by DarthBrady on 2010-01-25
Here's my situation:

I use Gnome (Ubuntu 9.10). I prefer it to KDE. I tried Kubuntu for a week or so, and I just had to switch back.

However, there was ONE think in KDE that I just can't live without. So I need to know if there is any way to make it work, or any existing piece of software like it, that I can use in Gnome.

The software i need is a KDE plasmoid widget called "Magic Folder". It puts a folder Icon on your desktop, that you can give custom Rules to, so if you drop a file in it, the "magic folder" will take that file and automatically move it to the any directory on your system you want it to, depending on the filetype.

For example, If you set the rules up for it, you could drop a .mp3 or an .ogg, and it would automatically move the file to your "music" directory, and so on.

This tool makes organising my files as I get them sooooo easy and saves a ton of time!!

Is there any way I can get this tool to work in Gnome? Or anything for gnome that does the same thing? I've been googling for days, with no luck.

---

### Post by kainalu on 2010-03-11
Im actually looking for this as well. Any clever coders know how?

Edit:

I don't know how personally but what if someone wrote a script that could do the same thing. Drop a file on it, and the script would launch, take the input (file), look at the file type, and move it. A pretty folder icon could be set as the icon for it. 
The only thing is, can a script be programmed to handle more than one file that way? If I drop 6 pictures and 4 torrent files on it at the same time, will it know how to sort each file?

---

### Post by kainalu on 2010-03-22
Try this.

Put this in your documents folder, make a panel launcher that has the type set to run in terminal, and point it at the script. When you want to clean your desktop, run it. It will clear any files not in a folder on your desktop. Modify to fit taste.

BEWARE: I throw away torrent files and windows executables when Im done with them, so my script does that too. It also throws away *~ backups, and 0 byte files. 

```

#!/bin/bash
#set -e
clear
echo "Sorting Desktop, Please be patient"

find ~/Desktop/ -maxdepth 1 -type f -iname "*" -empty \
	-exec mv {} ~/.local/share/Trash/files/ \; 2> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f -iname "*~" \
	-exec mv {} ~/.local/share/Trash/files/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" -o -iname "*.gif" \) \
	-exec mv {} ~/Pictures/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.pdf" -o -iname "*.doc" -o -iname "*.rtf" -o -iname "*.ott" -o -iname "*.ots" \
	 -o -iname "*.txt" -o -iname "*.odf" -o -iname "*.dot" -o -iname "*.odt" \) \
	-not -name "housekeepersnotes.txt" -exec mv {} ~/Documents/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.sh" -o -iname "*.bash" -o -iname "*.shell" -o -iname "*.script" \) -not -name "Cleanup.sh" \
	-exec mv {} ~/Documents/Scripts/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.mp3" -o -iname "*.m3u" -o -iname "*.ogg" -o -iname "*.wma" \) \
	-exec mv {} ~/Music/unsorted/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.flv" -o -iname "*.wmv" -o -iname "*.mpg" -o -iname "*.mp4" -o -iname "*.mpeg" \) \
	-exec mv {} ~/Videos/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.gz" -o -iname "*.tar.gz" -o -iname "*.gzip" -o -iname "*.zip" -o -iname "*.7zip" -o -iname "*.7" \
	-o -iname "*.7z" -o -iname "*.tar" -o -iname "*.deb" \) \
	-exec mv {} ~/zips/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.ISO" \) \
	-exec mv {} /repository/ISOs/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f \( -iname "*.exe" -o -iname "*.dll" -o -iname "*.com" -o -iname "*.js" -o -iname "*.torrent" \) \
	-exec mv {} ~/.local/share/Trash/files/ \; 2>> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f -iname "*" -not -name "Cleanup.sh" -not -name "housekeepersnotes.txt" \
	-exec mv {} /home/kainalu/Stuff\ im\ working\ on/sweep-up/ \; >> ~/Desktop/housekeepersnotes.txt

find ~/Desktop/ -maxdepth 1 -type f -iname "housekeepersnotes.txt" -empty \
	-exec rm {} \; 2> ~/Desktop/housekeepersnotes.txt


sleep 1s
clear
echo
echo
echo "All done! If the housekeeper had any notes for you,"
echo "they were left on your desk. Have a nice day!"
sleep 2s
exit 0

```

---

