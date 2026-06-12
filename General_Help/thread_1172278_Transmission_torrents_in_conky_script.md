---
title: "Transmission torrents in conky script"
date: 2009-05-28
forum: General Help
---

### Post by 987poiuytrewq on 2009-05-28
A script to display transmission torrents in your conky setup. To run, download the script, make it executable and put 
```
${execpi 1 ~/path/to/script}
```
(where the one is the update time in seconds) in your .conkyrc file. There are various settings to play around with if you like, and note that you need to install transmission-remote, and have the web interface of transmission enabled.

```
#! /bin/bash

#trim torrent name to this many characters
trim=20

#more settings further down marked with ========================


#get listing of all torrent info from transmission
# NOTE: you need to install transmission-cli AND UNINSTALL transmission-daemon
alltorrents=$(transmission-remote -l | sed -n -e '$b' -e '2,$p')


n=$(echo "$alltorrents" | wc -l)


#parse output to get data
#DO NOT EDIT THIS BIT
for i in `seq $n`
do
	torrent[$i]=$(echo "$alltorrents" | sed -n ''$i'p' | sed 's/   */\//g')

	progress[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $3}' | sed 's/%//')
	percent[$i]=$(echo 'scale=2; '${progress[$i]}'/100' | bc)
	have[$i]=$(echo  ${torrent[$i]} | awk -F/ '{print $4}')
	eta[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $5}')
	up[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $6}')
	down[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $7}')
	ratio[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $8}')
	status[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $9}')
	name[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $10}' )
	#trim and add ellipsis if too long
	if [ `echo ${name[$i]} | wc -m` -gt $trim ]
	then
		
		name[$i]=$(echo ${name[$i]} | cut -c -$trim)...
	fi
done

#convert status to symbols


#output data to conky, using standard conky formating

#some more settings=====================================================
#=======================================================================

#limit output to a certain number of torrents, all is a=$n first four is a=4 etc
a=$n

#progress bar length from right edge of conky
barlength=80

#change colours of listing depending on status and/or add icons
# icons are webding fonts eg pause symbol, down arrow etc
#CHANGE COLORS TO DESIRED OR COMMENT OUT IF NO COLORS WANTED
#movedown=$(echo '14*'$n | bc)
#echo '${voffset -'$movedown'}'

for i in `seq $a`
do
	case ${status[$i]} in
	"Idle")
		icon[$i]='${font Webdings};${font}' 
		color[$i]="B7B7B7"	
		;;
	"Stopped")
		icon[$i]='${font Webdings}<${font}' 
		color[$i]="B7B7B7"	
		;;
	"Up & Down")
		icon[$i]='${font Webdings}6${font}' 
		#color[$i]= 
		;;
	"Downloading")
		icon[$i]='${font Webdings}6${font}' 
		#color[$i]=
		;;
	"Seeding")
		icon[$i]='${font Webdings}5${font}'
		color[$i]='FFFFFF'
		;;
	*)
		;;
	esac

	#test to check we actually got some data back
if [ -z "$alltorrents" ] 
then
	#if not, print error message if you like, and exit
	#echo "Can't connect to transmission"
	exit
fi
#===================================================================

	#EDIT THE FOLLOWING BIT TO CONTROL DATA SEEN IN CONKY
	#enclose conky commands with ' '
	#enclose variables from this script with " " or nothing
	#in form ${name[$i]} where $i refers to the torrent number
	#possible variables are:
	#	progress	number 1-100 how much downloaded eg "45"
	#	percent		same but 0-1 eg "0.45"
	#	have		amount downloaded as string  eg "4.1 GB"
	#	eta		estimated time of arrival as string eg "4 hrs"
	#	up		transfer rate up in KB/s eg "21.1"
	# 	down		transfer rate down in KB/s eg "21.1"
	#	ratio		transfer ratio for torrent eg "0.88"
	#	status		eg "Downloading"
	#	icon		a small icon indicating status (see above 
	#			section)
	#	color		color depending on status (see above section)
	# 			eg "FF88AA" NB: must use exactly the format:
	# 			'${color '${color[$i]}'}' to apply the color to 
	#			a stretch of text, and remember to end it with
	#			'${color}'
	#	to draw the progress bar, use the exact command (incl single
	#	quotes)	'${execbar echo '${percent[%i]'}' and control the
	#	length with '${alignr '$barlength'}' where barlength defined above



	echo '${color '${color[$i]}'}''${font Sans:size=8}'"${name[$i]}"'${font sans:size=0}'
	echo ${icon[$i]}'${font Sans:size=7}'"${eta[$i]}"'${font}${alignr '$barlength'}${execbar echo '${percent[$i]}'}' '${color}' 

#===================================================================
done

```

---

### Post by sdlynx on 2010-02-07
This is great!

I haven't personally tested it, but if it does work like it should, you should post this in that new Conky Scripts thread.

---

### Post by parth115 on 2010-05-23
Works extremely well... excellent

---

### Post by Scooter_X on 2010-06-12
I try to run this, but I get an error: 

```
Conky: unknown variable fon
```

and then it just stops trying to run the conky...

ideas?

---

### Post by Caleb.Robertson on 2010-06-23
For me it wont do more then 2 torrents... anyone got any ideas?
 	Code:
 	Conky: unknown variable fon 
Getting the same thing.

---

### Post by Caleb.Robertson on 2010-06-24
Ok so i got it to stop giving me the error but... still only shows two torrents 

```
#! /bin/bash

#trim torrent name to this many characters
trim=15

#more settings further down marked with ========================


#get listing of all torrent info from transmission
# NOTE: you need to install transmission-cli AND UNINSTALL transmission-daemon
alltorrents=$(transmission-remote -l | sed -n -e '$b' -e '2,$p')


n=$(echo "$alltorrents" | wc -l)


#parse output to get data
#DO NOT EDIT THIS BIT
for i in `seq $n`
do
    torrent[$i]=$(echo "$alltorrents" | sed -n ''$i'p' | sed 's/   */\//g')

    progress[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $3}' | sed 's/%//')
    percent[$i]=$(echo 'scale=2; '${progress[$i]}'/100' | bc)
    have[$i]=$(echo  ${torrent[$i]} | awk -F/ '{print $4}')
    eta[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $5}')
    up[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $6}')
    down[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $7}')
    ratio[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $8}')
    status[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $9}')
    name[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $10}' )
    #trim and add ellipsis if too long
    if [ `echo ${name[$i]} | wc -m` -gt $trim ]
    then
        
        name[$i]=$(echo ${name[$i]} | cut -c -$trim)
    fi
done

#convert status to symbols


#output data to conky, using standard conky formating

#some more settings=====================================================
#=======================================================================

#limit output to a certain number of torrents, all is a=$n first four is a=4 etc
a=$n

#progress bar length from right edge of conky
barlength=75

#change colours of listing depending on status and/or add icons
# icons are webding fonts eg pause symbol, down arrow etc
#CHANGE COLORS TO DESIRED OR COMMENT OUT IF NO COLORS WANTED
#movedown=$(echo '14*'$n | bc)
#echo '${voffset -'$movedown'}'

for i in `seq $a`
do
    case ${status[$i]} in
    "Idle")
        icon[$i]='${font Webdings};${font}' 
        color[$i]="B7B7B7"    
        ;;
    "Stopped")
        icon[$i]='${font Webdings}<${font}' 
        color[$i]="B7B7B7"    
        ;;
    "Up & Down")
        icon[$i]='${font Webdings}6${font}' 
        #color[$i]= 
        ;;
    "Downloading")
        icon[$i]='${font Webdings}6${font}' 
        #color[$i]=
        ;;
    "Seeding")
        icon[$i]='${font Webdings}5${font}'
        color[$i]='FFFFFF'
        ;;
    *)
        ;;
    esac

    #test to check we actually got some data back
if [ -z "$alltorrents" ] 
then
    #if not, print error message if you like, and exit
    echo "Can't connect to transmission"
    exit
fi
#===================================================================
    #EDIT THE FOLLOWING BIT TO CONTROL DATA SEEN IN CONKY
    #enclose conky commands with ' '
    #enclose variables from this script with " " or nothing
    #in form ${name[$i]} where $i refers to the torrent number
    #possible variables are:
    #    progress    number 1-100 how much downloaded eg "45"
    #    percent        same but 0-1 eg "0.45"
    #    have        amount downloaded as string  eg "4.1 GB"
    #    eta        estimated time of arrival as string eg "4 hrs"
    #    up        transfer rate up in KB/s eg "21.1"
    #     down        transfer rate down in KB/s eg "21.1"
    #    ratio        transfer ratio for torrent eg "0.88"
    #    status        eg "Downloading"
    #    icon        a small icon indicating status (see above 
    #            section)
    #    color        color depending on status (see above section)
    #             eg "FF88AA" NB: must use exactly the format:
    #             '${color '${color[$i]}'}' to apply the color to 
    #            a stretch of text, and remember to end it with
    #            '${color}'
    #    to draw the progress bar, use the exact command (incl single
    #    quotes)    '${execbar echo '${percent[%i]'}' and control the
    #    length with '${alignr '$barlength'}' where barlength defined above
    echo "${name[$i]}"${percent[$i]}
    echo ${icon[$i]}"${eta[$i]}"


#===================================================================
done

```All I really changed was 
From this 
```
    echo '${color '${color[$i]}'}''${font Sans:size=8}'"${name[$i]}"'${font sans:size=0}'
    echo ${icon[$i]}'${font Sans:size=7}'"${eta[$i]}"'${font}${alignr '$barlength'}${execbar echo '${percent[$i]}'}' '${color}' 

```To this
```
    echo "${name[$i]}"${percent[$i]}
    echo ${icon[$i]}"${eta[$i]}"

```Taking out all the changing font commands, removed the error. I have all 5 torrents showing up on conky now, but its like it can only show or read so many char so it dumps the rest of the script. As you can see I had to cut a lot out the scrip. 

Anyone got any Ideas?

---

### Post by ktamm on 2010-07-18
I realize that I am a bit late to the party, however ... I think the config setting everyone is looking for is "text_buffer_size". The default is set at 256 characters which is why everyone is experiencing the cut off issues that sometimes mess conky up. Reading the description of the variable on this page ([http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)) has me hesitating to turn it up to much. I have modified my script to only spit out the last 5 torrents that are running and everything seems to be working correctly.

```
#! /bin/bash

#trim torrent name to this many characters
trim=45

#more settings further down marked with ========================


#get listing of all torrent info from transmission
# NOTE: you need to install transmission-cli AND UNINSTALL transmission-daemon
alltorrents=$(transmission-remote -l | sed -n -e '$b' -e '2,$p')


n=$(echo "$alltorrents" | wc -l)


#parse output to get data
#DO NOT EDIT THIS BIT
#for i in `seq $n`
for ((i=$n-4;i<=n;i++))
do
    torrent[$i]=$(echo "$alltorrents" | sed -n ''$i'p' | sed 's/   */\//g')

    progress[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $3}' | sed 's/%//')
    percent[$i]=$(echo 'scale=2; '${progress[$i]}'/100' | bc)
    have[$i]=$(echo  ${torrent[$i]} | awk -F/ '{print $4}')
    eta[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $5}')
    up[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $6}')
    down[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $7}')
    ratio[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $8}')
    status[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $9}')
    name[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $10}' )
    #trim and add ellipsis if too long
    if [ `echo ${name[$i]} | wc -m` -gt $trim ]
    then
        
        name[$i]=$(echo ${name[$i]} | cut -c -$trim)
    fi
done

#convert status to symbols


#output data to conky, using standard conky formating

#some more settings=====================================================
#=======================================================================

#limit output to a certain number of torrents, all is a=$n first four is a=4 etc
a=$n

#progress bar length from right edge of conky
barlength=100

#change colours of listing depending on status and/or add icons
# icons are webding fonts eg pause symbol, down arrow etc
#CHANGE COLORS TO DESIRED OR COMMENT OUT IF NO COLORS WANTED
#movedown=$(echo '14*'$n | bc)
#echo '${voffset -'$movedown'}'

#for i in `seq $a`
for ((i=$n-4;i<=n;i++))
do
    case ${status[$i]} in
    "Idle")
        icon[$i]='${font Webdings};${font}' 
        ;;
    "Stopped")
        icon[$i]='${font Webdings}<${font}' 
        ;;
    "Up & Down")
        icon[$i]='${font Webdings}6${font}' 
        ;;
    "Downloading")
        icon[$i]='${font Webdings}6${font}' 
        ;;
    "Seeding")
        icon[$i]='${font Webdings}5${font}'
        ;;
    *)
        ;;
    esac

    #test to check we actually got some data back
if [ -z "$alltorrents" ] 
then
    #if not, print error message if you like, and exit
    echo "Can't connect to transmission"
    exit
fi
#===================================================================
    #EDIT THE FOLLOWING BIT TO CONTROL DATA SEEN IN CONKY
    #enclose conky commands with ' '
    #enclose variables from this script with " " or nothing
    #in form ${name[$i]} where $i refers to the torrent number
    #possible variables are:
    #    progress    number 1-100 how much downloaded eg "45"
    #    percent        same but 0-1 eg "0.45"
    #    have        amount downloaded as string  eg "4.1 GB"
    #    eta        estimated time of arrival as string eg "4 hrs"
    #    up        transfer rate up in KB/s eg "21.1"
    #     down        transfer rate down in KB/s eg "21.1"
    #    ratio        transfer ratio for torrent eg "0.88"
    #    status        eg "Downloading"
    #    icon        a small icon indicating status (see above 
    #            section)
    #    color        color depending on status (see above section)
    #             eg "FF88AA" NB: must use exactly the format:
    #             '${color '${color[$i]}'}' to apply the color to 
    #            a stretch of text, and remember to end it with
    #            '${color}'
    #    to draw the progress bar, use the exact command (incl single
    #    quotes)    '${execbar echo '${percent[%i]'}' and control the
    #    length with '${alignr '$barlength'}' where barlength defined above

	echo "${name[$i]}"
	echo "${icon[$i]}""${eta[$i]}" '${alignr '$barlength'}${execbar echo '${progress[$i]}'}' 

#===================================================================
done
```

---

### Post by djyoung4 on 2010-07-21
> **ktamm said:**
> I realize that I am a bit late to the party, however ... I think the config setting everyone is looking for is "text_buffer_size". The default is set at 256 characters which is why everyone is experiencing the cut off issues that sometimes mess conky up. Reading the description of the variable on this page ([http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)) has me hesitating to turn it up to much. I have modified my script to only spit out the last 5 torrents that are running and everything seems to be working correctly.

```
#! /bin/bash

#trim torrent name to this many characters
trim=45

#more settings further down marked with ========================


#get listing of all torrent info from transmission
# NOTE: you need to install transmission-cli AND UNINSTALL transmission-daemon
alltorrents=$(transmission-remote -l | sed -n -e '$b' -e '2,$p')


n=$(echo "$alltorrents" | wc -l)


#parse output to get data
#DO NOT EDIT THIS BIT
#for i in `seq $n`
for ((i=$n-4;i<=n;i++))
do
    torrent[$i]=$(echo "$alltorrents" | sed -n ''$i'p' | sed 's/   */\//g')

    progress[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $3}' | sed 's/%//')
    percent[$i]=$(echo 'scale=2; '${progress[$i]}'/100' | bc)
    have[$i]=$(echo  ${torrent[$i]} | awk -F/ '{print $4}')
    eta[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $5}')
    up[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $6}')
    down[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $7}')
    ratio[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $8}')
    status[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $9}')
    name[$i]=$(echo ${torrent[$i]} | awk -F/ '{print $10}' )
    #trim and add ellipsis if too long
    if [ `echo ${name[$i]} | wc -m` -gt $trim ]
    then
        
        name[$i]=$(echo ${name[$i]} | cut -c -$trim)
    fi
done

#convert status to symbols


#output data to conky, using standard conky formating

#some more settings=====================================================
#=======================================================================

#limit output to a certain number of torrents, all is a=$n first four is a=4 etc
a=$n

#progress bar length from right edge of conky
barlength=100

#change colours of listing depending on status and/or add icons
# icons are webding fonts eg pause symbol, down arrow etc
#CHANGE COLORS TO DESIRED OR COMMENT OUT IF NO COLORS WANTED
#movedown=$(echo '14*'$n | bc)
#echo '${voffset -'$movedown'}'

#for i in `seq $a`
for ((i=$n-4;i<=n;i++))
do
    case ${status[$i]} in
    "Idle")
        icon[$i]='${font Webdings};${font}' 
        ;;
    "Stopped")
        icon[$i]='${font Webdings}<${font}' 
        ;;
    "Up & Down")
        icon[$i]='${font Webdings}6${font}' 
        ;;
    "Downloading")
        icon[$i]='${font Webdings}6${font}' 
        ;;
    "Seeding")
        icon[$i]='${font Webdings}5${font}'
        ;;
    *)
        ;;
    esac

    #test to check we actually got some data back
if [ -z "$alltorrents" ] 
then
    #if not, print error message if you like, and exit
    echo "Can't connect to transmission"
    exit
fi
#===================================================================
    #EDIT THE FOLLOWING BIT TO CONTROL DATA SEEN IN CONKY
    #enclose conky commands with ' '
    #enclose variables from this script with " " or nothing
    #in form ${name[$i]} where $i refers to the torrent number
    #possible variables are:
    #    progress    number 1-100 how much downloaded eg "45"
    #    percent        same but 0-1 eg "0.45"
    #    have        amount downloaded as string  eg "4.1 GB"
    #    eta        estimated time of arrival as string eg "4 hrs"
    #    up        transfer rate up in KB/s eg "21.1"
    #     down        transfer rate down in KB/s eg "21.1"
    #    ratio        transfer ratio for torrent eg "0.88"
    #    status        eg "Downloading"
    #    icon        a small icon indicating status (see above 
    #            section)
    #    color        color depending on status (see above section)
    #             eg "FF88AA" NB: must use exactly the format:
    #             '${color '${color[$i]}'}' to apply the color to 
    #            a stretch of text, and remember to end it with
    #            '${color}'
    #    to draw the progress bar, use the exact command (incl single
    #    quotes)    '${execbar echo '${percent[%i]'}' and control the
    #    length with '${alignr '$barlength'}' where barlength defined above

	echo "${name[$i]}"
	echo "${icon[$i]}""${eta[$i]}" '${alignr '$barlength'}${execbar echo '${progress[$i]}'}' 

#===================================================================
done
```

I tried your script and all I get is Can't connect to transmission
heres the terminal reading:
```
/home/home/conky/conkytransmission/conkytransmission.sh: line 11: transmission-remote: command not found
sed: invalid option -- '3'
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  --follow-symlinks
                 follow symlinks when processing in place
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

GNU sed home page: <http://www.gnu.org/software/sed/>.
General help using GNU software: <http://www.gnu.org/gethelp/>.
/home/home/conky/conkytransmission/conkytransmission.sh: line 22: torrent[$i]: bad array subscript
/home/home/conky/conkytransmission/conkytransmission.sh: line 47: status: bad array subscript

```
I can't figure out what is wrong

---

### Post by ktamm on 2010-07-22
My guess would be that you haven't followed the note saying: 

"NOTE: you need to install transmission-cli AND UNINSTALL transmission-daemon".

typing:
```

transmission-remote -l

```
(in a terminal) should show the torrents you currently have open

---

### Post by cerda on 2010-08-08
Thanks for the script !! working like a charm here. Is there a way to only show downloading torrents ?? i mean if one have a big list of torrents its not likely that they will show up on conky (script is showing the last 5 from transmission-remote -l).

Or maybe a way to configure transmission so downloading torrents would always be the last ones on the ID list

Thank you again for a great script!!

---

### Post by djyoung4 on 2010-08-12
Ok so I cant figure out how to move the rest of the torrent info over.  I tried changing between execpi, execi, exec, and execp but none of them work.  If anybody has any ideas it would be greatly appreciated.

---

### Post by ThomasB2k on 2010-08-28
Is there a way to display text like "No torrents" if there isn't any transmission activity?

---

