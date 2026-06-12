---
title: "[Solved]...MD5 gui for Gnome w/ Nautilus or Thunar"
date: 2009-01-05
forum: General Help
---

### Post by win_with_ben on 2009-01-05
This can be done, but it takes a little tinkering. I'm not aware of a standalone binary, so I will provide you with the scripts so you can right click on a file and have md5, sha1, sha256, tiger, and whirlpool hash digests pop-up automatically. First, you'll need a couple packages, md5deep and scite:

~: sudo apt-get md5deep scite

	Open scite (or you other favorite editor), paste in the following script, and save it to /home/username/.gnome2/nautilus-scripts/:
	
#! /bin/sh
tmp_file1="/tmp/md5"
tmp_file2="/tmp/sha1"
tmp_file3="/tmp/sha256"
tmp_file4="/tmp/tiger"
tmp_file5="/tmp/whirlpool"
md5deep       $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $tmp_file1
sha1deep       $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $tmp_file2
sha256deep   $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $tmp_file3
tigerdeep        $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $tmp_file4
whirlpooldeep $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $tmp_file5
scite "$tmp_file5" "$tmp_file4" "$tmp_file3" "$tmp_file2" "$tmp_file1"
sleep 3s
rm $tmp_file1
rm $tmp_file2
rm $tmp_file3
rm $tmp_file4
rm $tmp_file5
exit 0

	Name it 'Hash', and BE SURE to make it executable with 'chmod +x Hash' or use right click>properties> permissions. Now when you right click on a file (using the Nautilus file manager) you should see a Scripts> entry which opens to reveal Hash. Click it after selecting a file (not a directory) and you should have a Scite window come up w/ five tabs labeled by hash algorithm and containg the calculated hash, along with the path to the file used. One down side: File_Names_Cannot_Contain_Spaces. Either rename your files, use md5sum at the command line, or you can use Thunar. Thunar can handle file names w/ spaces using this method:
	
	Using Thunar: go to Edit>Configure custom actions>Add action. Give it a name and description. Now time to paste in the command. You'll need to re-open the script we used above, and make a couple smalll changes. Work on a copy so the original script will still work with Nautilus.
	1. Delete the first line (#! /bin/sh)
	2. Where ever you see $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS replace that with %f
	3. Now copy and paste the whole thing into the Command box.
	4. Select all the boxes under Appearance conditions, and click ok.
Now when you right click on a file in Thunar, you'll have the option to calculate the hashes under the name you gave your custom action.
	One last thing. If you don't get all five tabs pop up in Scite, you may need to enbale it in your global options. Hope this works for you. I think it's freakin sweet!

---

### Post by IQAndreas on 2011-12-01
Will this script work with Gnome 3 and the latest version of Nautilus, or does it need to be tweaked?

---

