---
title: "zenity and loops real problem"
date: 2008-09-28
forum: Desktop Environments
---

### Post by kantor on 2008-09-28
I write this scrips to automately check the ink's levels of my printer. I would the script to work that way:

0) sleep until the printer is on
1) tell a warning about the ink that reach less than 5% level at the last check
2) read the new levels
3) put the level in a notification on the taskbar
4) recheck the levels after a time of sleep or go to sleep at point 0 when printer goes off

The thing is, i put a lots of commands in a endless loop... but when zenity --notification is running there's no way to continue the loop. I mean with or without the --listen option.

This is the code:

```
#!/bin/bash

while true; do

	while [ ! -e /dev/usb/lp0 ]; do
		# Sleep until the printer device file is created
		sleep 1
	done

	sleep 30s
        
        #it tells about the ink's that was at less than 5% level at last check 
	if espeak -p 90 -v it "`cat warn`"
		then
		zenity --error --text="/dev/dsp busy problem with telling remind warnings about exausted inkpack checked at the last check"
	fi

        
	while [ -e /dev/usb/lp0 ]; do
                #it reads the level of the ink's in the printer and if it is lower 
                #than 5% it change inkstat to make note of the need to change the  
                #inkpack
		escputil -r /dev/usb/lp0 -i>status
	
		inkstat=0000
		num=5
	
                #this next commands extract the value of percentage level of Cyan
		string=`less status|grep Cyan`
		clev=`echo ${string:39}`
		if [ $clev -le $num ]
			then
			let "inkstat += 1"
		fi
	        
                #this is for yellow
		string=`less status|grep Yellow`
		ylev=`echo ${string:39}`
		if [ $ylev -le $num ] 
			then
			let "inkstat += 10"
		fi

                #and so on...
		string=`less status|grep Magenta`
		mlev=`echo ${string:39}`
		if [ $mlev -le $num ]
			then
			let "inkstat += 100"
		fi
	
		string=`less status|grep Black`
		blev=`echo ${string:39}`
		if [ $blev -le $num ]
			then
			let "inkstat += 1000"
		fi
	
		echo $inkstat>levs
		echo Cyan $clev%>>levs
		echo Yellow $ylev%>>levs
		echo Magenta $mlev%>>levs  
		echo Black $blev%>>levs
                
                #now the inkstat variable contains all the informations about the
                #levels of inks in the printer
                #and these commands write a warning about the inkpacks that needs to 
                #be changed
		case "$inkstat" in
			1111) 
		 		echo "Change  all">warn
		 		;;
			1110) 
		 		echo "Change  Black, Magenta and Yellow">warn
		 		;;
			1101) 
		 		echo "Change  Black, Magenta and Cyan">warn
		 		;;
			1011) 
		 		echo "Change  Black, Yellow and Cyan">warn
		 		;;
			111) 
				echo "Change  Magenta, Yellow and Cyan">warn
				;;
			1100) 
				 echo "Change  Black and Magenta">warn
				;;
			1010) 
		 		echo "Change  Black and Yellow">warn
		 		;;
			1001) 
		 		echo "Change  Black and Cyan">warn
		 		;;
			110) 
		 		echo "Change  Magenta and Yellow">warn
		 		;;
			101) 
		 		echo "Change  Magenta and Cyan">warn
		 		;;
			11) 
		 		echo "Change  Yellow and Cyan">warn
		 		;;
			1000) 
		 		echo "Change  Black">warn
		 		;;
			100) 
		 		echo "Change  Magenta">warn
		 		;;
			10) 
		 		echo "Change  Yellow">warn
		 		;;
			1) 
		 		echo "Change  Cyan">warn
		 		;;
			*)
		 		echo "All ok">warn
		 		;;
		esac
		
                #this added a warning at the end of levs file 	
		cat warn>>levs
                #and here is the problem, this command create a notification and the loop doesn't go on.
		zenity --notification --listen --window-icon="info" --text="`cat levs`"
		sleep 30m
	done
done
```

---

### Post by kantor on 2008-09-28
solved, this is the working code in italian:

```
#!/bin/bash

exec 3> >(zenity --notification --text="Stampante spenta" --listen)

while true; do
	if [ ! -e /dev/usb/lp0 ]; then
		echo "icon:info" >&3
		echo "tooltip:Stampante spenta" >&3
	fi

	while [ ! -e /dev/usb/lp0 ]; do
		# Sleep until the printer device file is created
		sleep 1s
	done

	echo "icon:info" >&3
	echo "message:Stampante accesa, verifica stato attuale degli inchiostri della stampante in corso" >&3
	echo "tooltip:Situazione degli inchiostri da ultima scansione:`cat warn`" >&3

#	if espeak -p 90 -v it "`cat warn`"
#		then
#	echo "icon:error" >&3		
#	echo "message:Scheda audio occupata da un\'altra applicazione, impossibile comunicare verbalmente la situazione dei # livelli d'inchiostro" >&3
#	fi	

	sleep 30s

	while [ -e /dev/usb/lp0 ]; do
		escputil -r /dev/usb/lp0 -i>status
	
		inkstat=0000
		num=5
	
		string=`less status|grep Cyan`
		clev=`echo ${string:39}`
		if [ $clev -le $num ]
			then
			let "inkstat += 1"
		fi
	
		string=`less status|grep Yellow`
		ylev=`echo ${string:39}`
		if [ $ylev -le $num ] 
			then
			let "inkstat += 10"
		fi

		string=`less status|grep Magenta`
		mlev=`echo ${string:39}`
		if [ $mlev -le $num ]
			then
			let "inkstat += 100"
		fi
	
		string=`less status|grep Black`
		blev=`echo ${string:39}`
		if [ $blev -le $num ]
			then
			let "inkstat += 1000"
		fi
	
		echo $inkstat>levs
		echo Ciano $clev%>>levs
		echo Giallo $ylev%>>levs
		echo Magenta $mlev%>>levs  
		echo Nero $blev%>>levs
	
		case "$inkstat" in
			1111) 
		 		
				echo "Cambiare tutte le cartucce">warn
		 		;;
			1110) 
		 		echo "Cambiare Nero, Magenta e Giallo">warn
		 		;;
			1101) 
		 		echo "Cambiare Nero, Magenta e Ciano">warn
		 		;;
			1011) 
		 		echo "Cambiare Nero, Giallo e Ciano">warn
		 		;;
			111) 
				echo "Cambiare Magenta, Giallo e Ciano">warn
				;;
			1100) 
				echo "Cambiare Nero e Magenta">warn
				;;
			1010) 
		 		echo "Cambiare Nero e Giallo">warn
		 		;;
			1001) 
		 		echo "Cambiare Nero e Ciano">warn
		 		;;
			110) 
		 		echo "Cambiare Magenta e Giallo">warn
		 		;;
			101) 
		 		echo "Cambiare Magenta e Ciano">warn
		 		;;
			11) 
		 		echo "Cambiare Giallo e Ciano">warn
		 		;;
			1000) 
		 		echo "Cambiare Nero">warn
		 		;;
			100) 
		 		echo "Cambiare Magenta">warn
		 		;;
			10) 
		 		echo "Cambiare Giallo">warn
			 	;;
			1) 
		 		echo "Cambiare Ciano">warn
		 		;;
			*)
		 		echo "Tutto apposto">warn
		 		;;
		esac
			
		cat warn>>levs
		
		if [ $inkstat -eq 0 ]
		then
			echo "icon:info" >&3
		else
			echo "icon:warning" >&3
		fi			
			echo "tooltip:"`cat levs`"" >&3

		sleep 30m
	done
done
```

this link has been very useful for me, i saw a very poor documentation about zenity and even less about zenity --notification [http://ubuntuforums.org/showthread.php?t=873796]("http://ubuntuforums.org/showthread.php?t=873796")

---

