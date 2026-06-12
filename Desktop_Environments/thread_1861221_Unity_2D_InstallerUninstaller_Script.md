---
title: "Unity 2D Installer/Uninstaller Script"
date: 2011-10-15
forum: Desktop Environments
---

### Post by Itehnological on 2011-10-15
This is an install and uninstall bash script for UNITY 2D. I made this because when I use my computer for programming I prefer the standard gnome look of the Ubuntu Desktop OS, but when I use it only to browse online or just chack something I prefer Unity. So I made this script for easy installing and uninstalling of Unity 2D.

Hope you like it!

This is a very useful script for those who use the outdated video driver and get something like this, when they run '/usr/lib/nux/unity_support_test -p':
'Not blacklisted: no'


**HOW TO USE?**
Just run it from a terminal and follow the instructions ..
You just need to confirm and choose the mode.
Everything else is done automatically.


```

clear
echo "What do you want to do?"
select yn in "INSTALL Unity 2D" "REMOVE Unity 2D"; do
    case $yn in
        "INSTALL Unity 2D" ) 
		# Here we start the installation pocedure

		clear
		echo "Are you sure you want to install UNITY 2D?"
		select yn in "Yes" "No"; do
		    case $yn in
		        Yes )
				read -p  "Press ENTER to continue with installation ..."
				sudo apt-get install unity-2d
		
				# Prompt for rebooting
				clear
				echo "Activating of UNITY 2D requires your computer to be rebooted. Do you wish to reboot your computer now?"
				select yn in "Yes" "No"; do
				    case $yn in
				        Yes )
						read -p  "Press ENTER to REBOOT ..."
						sudo reboot
						break;;
				        No )
						echo "Reboot canceled. Unity 2D will be activated the next time you restart your computer."
						exit;break;;
				    esac
				done
	
				# END Prompt for rebooting

				break;;
		        No )
				echo "Installation canceled."
				exit;break;;
		    esac
		done
		

		# END Installation procedure	

		break;;
        "REMOVE Unity 2D" ) 
		
		# Removing procedure
		clear
		echo "Are you sure you want to remove UNITY 2D?"
		select yn in "Yes" "No"; do
		    case $yn in
		        Yes )
				sudo apt-get purge unity-2d

				# Prompt for rebooting
				clear
				echo "To fully remove Unity 2d you need to reboot your computer. Do you wish to reboot your computer now?"
				select yn in "Yes" "No"; do
				    case $yn in
				        Yes )
						read -p  "Press ENTER to REBOOT ..."
						sudo reboot
						break;;
				        No )
						echo "Reboot canceled. Unity 2D will be activated the next time you restart your computer."
						exit;break;;
				    esac
				done
	
				# END Prompt for rebooting

				break;;
		        No )
				echo "Operation canceled."
				exit;break;;
		    esac
		done
		# END Removing procedure

		exit;break;;
    esac
done

```

---

