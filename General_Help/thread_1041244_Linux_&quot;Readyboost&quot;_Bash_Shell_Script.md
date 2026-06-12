---
title: "Linux &quot;Readyboost&quot; Bash Shell Script"
date: 2009-01-16
forum: General Help
---

### Post by akimatsu123 on 2009-01-16
This is a shell script that can be used to star the the Linux equivalent of Vista's "Readyboost" feature. It configures your computer to use your external USB, SD, or any other disks as swap space, with higher priority than your HD swap space)

I do not claim credit for the technique itself. It was taken from this tutorial: [http://ubuntuforums.org/showthread.php?t=395435]("http://ubuntuforums.org/showthread.php?t=395435")

Here is the script:

```
#!/bin/bash

echo "Ubuntu Linux Readyboost Feature"
echo "-------------------------------"

RB_ON()
{
	clear
	echo "Turning Readyboost ON"
	sudo umount /dev/$device
	echo "----------------------"
	sudo fdisk -l
	echo "----------------------"
	read -p "Enter the device name (eg. \"sda1\") : " device
	sudo mkswap /dev/$device
	sudo swapon -p 32767 /dev/$device
	echo "---------------------------------------------------------------"
	echo "Please confirm that system has turned on Readyboost (/dev/$device)"
	cat /proc/swaps
}

RB_OFF()
{
	clear
	echo "Turning Readyboost OFF"
	echo "----------------------"
	sudo fdisk -l
	echo "----------------------"
	read -p "Enter the device name (eg. \"sda1\") : " device
	sudo swapoff /dev/$device
	echo "---------------------------------------------------------------"
	echo "Please confirm that system has turned on Readyboost (/dev/$device)"
	cat /proc/swaps
}

input()
{
	echo "1. Turn ON Readyboost"
	echo "2. Turn OFF Readyboost"
	echo "3. Quit"
	read -p "Action: " answer
}

input

case $answer in

1)
	RB_ON;;
2)
	RB_OFF;;
3)
	exit;;
*)
	echo "Invalid Input"
	echo "-------------------------"
	input
esac
```

---

