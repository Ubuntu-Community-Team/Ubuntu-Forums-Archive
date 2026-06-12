---
title: "Script updating wallpaper help"
date: 2010-03-20
forum: Desktop Environments
---

### Post by Jakey_TheSnake on 2010-03-20
So I'm following this simple tutorial: [http://www.omgubuntu.co.uk/2009/09/real-earth-wallpaper-linux.html](http://www.omgubuntu.co.uk/2009/09/real-earth-wallpaper-linux.html) 

The script that it uses downloads an updated version of the image, but it does so far too often (you can see this by running it in the terminal). I would like to edit it so that it updates every 15 minutes. 

The original script is this: 

```
#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 60 ]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		temp=$(stat -c%s world.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_Wallpaper.jpg
				mv world.jpg world_sunlight_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 3600
done
```

Thanks, I have no experience with bash :p and my upping the sleep commands seems to have done nothing :l

---

### Post by mechro on 2010-03-20
Edit... never mind... sorry.

---

### Post by ldouble_e on 2010-03-21
#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
    COUNTER=0
    while [  $COUNTER -lt 60 ]; do
        wget [http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg) -O world.jpg
        temp=$(stat -c%s world.jpg)
        if [[ $temp > 1000 ]]
            then     rm world_sunlight_Wallpaper.jpg
                mv world.jpg world_sunlight_Wallpaper.jpg
                break
        fi
        sleep 900
            COUNTER=$((COUNTER + 1)) 
    done
    sleep 3600
done

I took out the LET statement and changed it to COUNTER=$((COUNTER + 1)) then I increased the sleep to 900 seconds which is 15 minutes. The original script was updating every 5 seconds. I also suspect you were getting an "error let: not found" you were unaware of, which will be corrected with the new COUNTER=$((COUNTER +1)). This script will now change the desktop every 15 minutes  for 15 hours, then it will sleep for an hour and start over. I'm a novice at scripting, but this script is poorly written in my opinion. There's a lot of room for errors. Also when you do the chmod command instead of +x I'd use 'sudo chmod 755 changer.sh' which gives root full access and users and group read and execute access without the need to pull up the permissions on the file to verify who has what permission. I hope this helps. Good luck!

---

### Post by Jakey_TheSnake on 2010-03-21
Thanks, that solved it. I tried upping the *other* sleep time before, and I have no idea why that didn't work, but this one does so oh well. 

The error changes slightly, it now reads: ```
changer.sh: 18: [[: not found

```

But it doesn't seem to affect the script at all, so I'm all for just leaving it :P

---

