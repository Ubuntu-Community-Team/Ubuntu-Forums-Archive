---
title: "Docplastic's Handy Nautilus Scripts"
date: 2009-01-08
forum: General Help
---

### Post by docplastic on 2009-01-08
This is a list of my most used Gnome Nautilus scripts.
I automatically (re)generate this list using the following one line command:
(rm nautilus-scripts-$(date +%G%m%d);echo -e "# docplastic's nautilus scripts: MAIN\n"; echo "#### docplastic's nautilus scripts: MAIN ###" >>nautilus-scripts-$(date +%G%m%d); for i in $HOME/.gnome2/nautilus-scripts/*;do echo -e "\n### $i\n# --- cut here ---" >>nautilus-scripts-$(date +%G%m%d) && cat $i >>nautilus-scripts-$(date +%G%m%d) && echo -e "# --- cut here ---" >>nautilus-scripts-$(date +%G%m%d);done;echo -e "# docplastic's nautilus scripts: OTHER\n"; echo -e "\n\n#### docplastic's nautilus scripts: OTHER ###" >>nautilus-scripts-$(date +%G%m%d); for i in $HOME/.gnome2/nautilus-scripts/other/*;do echo -e "\n### $i\n# --- cut here ---" >>nautilus-scripts-$(date +%G%m%d) && cat $i >>nautilus-scripts-$(date +%G%m%d) && echo -e "# --- cut here ---" >>nautilus-scripts-$(date +%G%m%d);done)

#### docplastic's nautilus scripts: MAIN ###

### /home/jdesk/.gnome2/nautilus-scripts/a2ps-pdf
# --- cut here ---
#!/bin/sh -e
#
# convert a .ps file into a (A4) .pdf file
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/a2ps"
NEEDPACK="a2ps"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi
fi
PDFTYPE="1.4"
OPTIONS="-sPAPERSIZE=a4"
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tfile=${FILE##*/} && tfile=${tfile%.*}
	##/usr/bin/ps2pdf "$(echo $FILE)" "${FILE%/*}/$tfile.pdf"
	# exec $NEEDBIN  $OPTIONS -q -dNOPAUSE -dBATCH  -dSAFER \
	#-dCompatibilityLevel="$PDFTYPE" \
	#-sDEVICE=pdfwrite -sOutputFile="${FILE%/*}/$tfile.pdf" \
	#$OPTIONS -c .setpdfwrite  -f "$FILE"
	exec $NEEDBIN -1P pdf "$FILE"
	#exec $NEEDBIN --medium=A4 -1P pdf "$FILE"
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/a2ps-ps
# --- cut here ---
#!/bin/sh -e
#
# convert a .pdf file into a (A4) .ps file using a2ps tools package
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/a2ps"
NEEDPACK="a2ps"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit;
	fi ;
fi;
#printer="`lpstat -d | sed 's/\(.*\)system default destination: /\1/'`"
printer=$(lpstat -d | sed 's/\(.*\): \(.*\)/\2/')
#file=$(echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\\ /g') ;
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tfile=${FILE##*/} && tfile=${tfile%.*}
	exec $NEEDBIN -1 --medium=A4 -o ${FILE%/*}/$tfile.ps -- $FILE
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/copy-to
# --- cut here ---
#!/bin/sh -e
#
# Copy selected files/folders to an user selected directory
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
targetdir=$(zenity --file-selection --directory --title "${0##*/} which Location?")
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	targetfile=$targetdir/${FILE##*/}
	if [ -x $targetdir -a -w $targetdir ] ; then
		if [ -e $targetfile ] ; then
			if  [ $(zenity --question --title "${0##*/}..." --text "$targetfile\nDestination exists. Overwrite ?"; echo $?) ] ; then
				rm -fr $targetfile
				cp -ar $FILE $targetdir
				if (( $? != 0 )); then
					zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
				fi
			fi
		else
			cp -ar $FILE $targetdir
			if (( $? != 0 )); then
				zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
			fi
		fi
	else
		zenity --info --title "${0##*/} Error" --text "Error: destination directory is not accessible"
	fi
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/exif-rename
# --- cut here ---
#!/bin/sh
#
# Renames photos using exif info.
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/exiftool"
NEEDPACK="libimage-exiftool-perl"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit;
	fi ;
fi;
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	mv $FILE $($NEEDBIN -T '-FileName<${CreateDate}' -d "%y%m%d-%H%M%S%%.c.%%le" $FILE)
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/fprint-bw
# --- cut here ---
#!/bin/sh -e
#
# fprint: fineprint-like utility to duplex print a .ps files into A5 booklets.
#  prints front and rear, even in plain (non duplex) printers;
#  accepts a .ps file and modifies it, compressing
#  and rotating each two A4 pages into a single A4 sheet;
#  prints front (odd) pages first and then waits for you to
#  reinsert the printed paper. Once paper reinserted it will
#  print rear (even) pages.
#  you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2008 by J. Antas.
# Released under a GPL 2.0 License (full text available
# at [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html))
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/psbook"
NEEDPACK="psutils"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi 
fi
#printer=$(lpstat -d | sed -rn 's/.* ([^ ]+)/\1/p') # get DEFAULT PRINTER
printer=$(lpstat -d | sed 's/\(.*\) \(.*\)/\2/') # get DEFAULT PRINTER
file=$(echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\\ /g') 
tmpfile=$(mktemp)
$NEEDBIN $file | /usr/bin/pstops -q -p a4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" > $tmpfile
	#$NEEDBIN $FILE | /usr/bin/psnup -p a4 -2 -q > $tmpfile # an alternative solution
/usr/bin/lpr -P $printer -o page-set=odd -o outputorder=reverse $tmpfile
if zenity --question --title="Fine Printing to $printer..." --text="Printing $file\nPrinting odd pages first,\nWhen finished load the paper back in and click OK"; then
	/usr/bin/lpr -P $printer -o page-set=even -o outputorder=reverse $tmpfile
fi 
killall zenity
[ -f $tmpfile ] && /bin/rm $tmpfile
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/fprint-bw-new
# --- cut here ---
#!/bin/sh -e
#
# fprint: fineprint-like utility to duplex print a .ps files into A5 booklets.
#  prints front and rear, even in plain (non duplex) printers;
#  accepts a .ps file and modifies it, compressing
#  and rotating each two A4 pages into a single A4 sheet;
#  prints front (odd) pages first and then waits for you to
#  reinsert the printed paper. Once paper reinserted it will
#  print rear (even) pages.
#  you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2008 by J. Antas.
# Released under a GPL 2.0 License (full text available
# at [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html))
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/psbook"
NEEDPACK="psutils"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi 
fi
#printer=$(lpstat -d | sed -rn 's/.* ([^ ]+)/\1/p') # get DEFAULT PRINTER
printer=$(lpstat -d | sed 's/\(.*\) \(.*\)/\2/') # get DEFAULT PRINTER
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tmpfile=$(mktemp)
	file=$FILE
	#file=$(echo $FILE | sed -e 's/\%20/\\ /g')
	#zenity --info --title "${0##*/}" --text "\$file: $file\n\$tmpfile: $tmpfile\n\$printer: $printer"

	$NEEDBIN $file | /usr/bin/psnup -p a4 -2 -q > $tmpfile
	#$NEEDBIN $file | /usr/bin/pstops -q -p a4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" > $tmpfile

	/usr/bin/lpr -P $printer -o Quality:normal -o page-set=odd -o outputorder=reverse $tmpfile
	if zenity --question --title="Fine Printing to $printer..." --text="Printing $file\nPrinting odd pages first,\nWhen finished load the paper back in and click OK"; then
		/usr/bin/lpr -P $printer -o Quality:normal -o page-set=even -o outputorder=reverse $tmpfile
	fi
	killall zenity
done
[ -f $tmpfile ] && /bin/rm $tmpfile
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/fprint-color
# --- cut here ---
#!/bin/sh -e
#
# fprint: fineprint-like utility to duplex print a .ps files into A5 booklets.
#  prints front and rear, even in plain (non duplex) printers;
#  accepts a .ps file and modifies it, compressing
#  and rotating each two A4 pages into a single A4 sheet;
#  prints front (odd) pages first and then waits for you to
#  reinsert the printed paper. Once paper reinserted it will
#  print rear (even) pages.
#  you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2008 by J. Antas.
# Released under a GPL 2.0 License (full text available
# at [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html))
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/psbook"
NEEDPACK="psutils"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi
fi
#
#printer="okic3300n-color" # SELECT PRINTER from those found with: lpstat -a
printer=$(lpstat -a | sed -rn '/color/s/([^ ]+) .*/\1/p') # choose a COLOR printer
#
file=$(echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g' -e 's/\%20/\\ /g') ;
tmpfile=$(mktemp)
$NEEDBIN $file | /usr/bin/pstops -q -p a4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" > $tmpfile
/usr/bin/lpr -P $printer -o page-set=odd -o outputorder=reverse $tmpfile
if zenity --question --title="Fine Printing to $printer..." --text="Printing $file\nPrinting odd pages first,\nWhen finished load the paper back in and click OK"; then
	/usr/bin/lpr -P $printer -o page-set=even $tmpfile
fi
killall zenity
[ -f $tmpfile ] && /bin/rm $tmpfile
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/fprint-color-new
# --- cut here ---
#!/bin/sh -e
#
# fprint: fineprint-like utility to duplex print a .ps files into A5 booklets.
#  prints front and rear, even in plain (non duplex) printers;
#  accepts a .ps file and modifies it, compressing
#  and rotating each two A4 pages into a single A4 sheet;
#  prints front (odd) pages first and then waits for you to
#  reinsert the printed paper. Once paper reinserted it will
#  print rear (even) pages.
#  you may fold the printed sheets to form an A5 booklet;
#
# Copyright © 2005-2008 by J. Antas.
# Released under a GPL 2.0 License (full text available
# at [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html))
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/psbook"
NEEDPACK="psutils"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi 
fi
#printer="okic3300n-color" # SELECT PRINTER from those found with: lpstat -a
printer=$(lpstat -a | sed -rn '/color/s/([^ ]+) .*/\1/p') # choose a COLOR printer
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tmpfile=$(mktemp)
	file=$FILE
	#file=$(echo $FILE | sed -e 's/\%20/\\ /g')
	#zenity --info --title "${0##*/}" --text "\$file: $file\n\$tmpfile: $tmpfile\n\$printer: $printer"

	$NEEDBIN $file | /usr/bin/psnup -p a4 -2 -q > $tmpfile
	#$NEEDBIN $file | /usr/bin/pstops -q -p a4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)" > $tmpfile

	/usr/bin/lpr -P $printer -o page-set=odd -o outputorder=reverse $tmpfile
	if zenity --question --title="Fine Printing to $printer..." --text="Printing $file\nPrinting odd pages first,\nWhen finished load the paper back in and click OK"; then
		/usr/bin/lpr -P $printer -o page-set=even -o outputorder=reverse $tmpfile
	fi
	killall zenity
done
[ -f $tmpfile ] && /bin/rm $tmpfile
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/link-to
# --- cut here ---
#!/bin/sh -e
#
# Link selected files/folders to an user selected directory
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
targetdir=$(zenity --file-selection --directory --title "${0##*/} which Location?")
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	targetfile=$targetdir/${FILE##*/}
	if [ -x $targetdir -a -w $targetdir ] ; then
		if [ -e $targetfile ] ; then
			if  [ $(zenity --question --title "${0##*/}..." --text "$targetfile\nDestination exists. Overwrite ?"; echo $?) ] ; then
				#ln -sf $FILE $targetdir
				ln -sf $FILE $targetfile
				if (( $? != 0 )); then
					zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
				fi
			fi
		else
			#ln -s $FILE $targetdir
			ln -s $FILE $targetfile
			if (( $? != 0 )); then
				zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
			fi
		fi
	else
		zenity --info --title "${0##*/} Error" --text "Error: destination directory is not accessible"
	fi
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/lower-case
# --- cut here ---
#!/bin/sh -e
#
# lowercase: Renames input FILE to lowercase.
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	new=${FILE%/*}/$(echo ${FILE##*/} | tr "A-ZÇÃÁÂÀÉÊÈÍÌÕÓÔÒÚÙ" "a-zçãáâàéêèíìõóôòúù")
	[ -e $new ] || mv $FILE $new
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/move-to
# --- cut here ---
#!/bin/sh -e
#
# Move selected files/folders to an user selected directory
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
targetdir=$(zenity --file-selection --directory --title "${0##*/} which Location?")
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	targetfile=$targetdir/${FILE##*/}
	if [ -x $targetdir -a -w $targetdir ] ; then
		if [ -e $targetfile ] ; then
			if  [ $(zenity --question --title "${0##*/}..." --text "$targetfile\nDestination exists. Overwrite ?"; echo $?) ] ; then
				rm -fr $targetfile
				mv -f $FILE $targetdir
				if (( $? != 0 )); then
					zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
				fi
			fi
		else
			mv $FILE $targetdir
			if (( $? != 0 )); then
				zenity --info --title "${0##*/} Error" --text "Error: unable to ${0##*/} destination"
			fi
		fi
	else
		zenity --info --title "${0##*/} Error" --text "Error: destination directory is not accessible"
	fi
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/name-normalizer
# --- cut here ---
#!/bin/sh -e
#
# Change file name, replacing unorthodox characters
# test string: ÇÃÉºÇª(c)v__<w:x'y&#65533;--z>|A\b!Ç"d#É$f%G&I(j)k=M?l»m«n\[o]
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	new=${FILE%/*}/$(echo ${FILE##*/} | tr -s " &#65533;" "_" | tr -s "_-" "_-" | tr -d '[ºª:[+{},;"=?~()<>&*|$#]%\\]' | tr -d "»«&#65533;!'" | tr "A-ZÇÃÁÂÀÉÊÈÍÌÕÓÔÒÚ" "a-zçãáâàéêèíìõóôòú")
	[ -e $new ] || mv $FILE $new	
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/other
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/pdf2ps
# --- cut here ---
#!/bin/sh -e
#
# convert a .pdf file into a (A4) .ps file using ghostscript tools package
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/gs"
NEEDPACK="ghostscript"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit;
	fi ;
fi;
OPTIONS="-sPAPERSIZE=a4"
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tfile=${FILE##*/} && tfile=${tfile%.*}
	exec "$NEEDBIN" $OPTIONS -q -dNOPAUSE -dBATCH -dSAFER \
	-sDEVICE=pswrite "-sOutputFile=${FILE%/*}/$tfile.ps" \
	$OPTIONS -c save pop -f "$FILE"
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/ps2pdf
# --- cut here ---
#!/bin/sh -e
#
# convert a .ps file into a (A4) .pdf file
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
IFS="
"
NEEDBIN="/usr/bin/gs"
NEEDPACK="ghostscript"
if [ ! -x $NEEDBIN ] ; then
	if zenity --question --title="$0 Error: uninstalled dependencies" --text="$0 needs the $NEEDPACK package which is not installed\n\nTo install $NEEDPACK click OK"; then
		sudo aptitude -R install $NEEDPACK | zenity --progress --pulsate --auto-close --text="Installing $NEEDPACK..."
	else
		exit
	fi
fi
PDFTYPE="1.4"
OPTIONS="-sPAPERSIZE=a4"
for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
	tfile=${FILE##*/} && tfile=${tfile%.*}
	##/usr/bin/ps2pdf "$(echo $FILE)" "${FILE%/*}/$tfile.pdf"
	exec $NEEDBIN  $OPTIONS -q -dNOPAUSE -dBATCH  -dSAFER \
	-dCompatibilityLevel="$PDFTYPE" \
	-sDEVICE=pdfwrite -sOutputFile="${FILE%/*}/$tfile.pdf" \
	$OPTIONS -c .setpdfwrite  -f "$FILE"
done
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/root-gedit
# --- cut here ---
#!/bin/sh
#
# Open a file with Gedit with root previleges
#
foo=`gksudo -u root -k -m "enter your password for Gedit root access" /bin/echo "root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/root-nautilus
# --- cut here ---
#!/bin/sh
#
# Open a Nautilus file browser with root previleges
#
foo=`gksudo -u root -k -m "enter your password for Nautilus root access" /bin/echo "root access?"`
# we should not run graphical tools using sudo as there is a user's dbus session running.
# we can use dbus-launch to workaround the issue
/usr/bin/gksu "dbus-launch nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/search-here
# --- cut here ---
#!/bin/sh
#
# Open a gnome search window in the selected directory.
#
# make this script executable and copy it to ~/.gnome2/nautilus-scripts/
#
/usr/bin/gnome-search-tool --path=$(echo $NAUTILUS_SCRIPT_CURRENT_URI | sed -e 's/file:\/\///')
# --- cut here ---

### /home/jdesk/.gnome2/nautilus-scripts/terminal-here
# --- cut here ---
#!/bin/sh
#
# Open a gnome-terminal in the selected directory.
#
# copy to ~/.gnome2/nautilus-scripts/
#
/usr/bin/gnome-terminal --working-directory=$(echo $NAUTILUS_SCRIPT_CURRENT_URI | sed -e 's/file:\/\///')
# --- cut here ---

---

