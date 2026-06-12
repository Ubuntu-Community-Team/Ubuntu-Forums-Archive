---
title: "Live earth wallpaper"
date: 2010-06-21
forum: Desktop Environments
---

### Post by jakupl on 2010-06-21
I made a script that automatically configures your desktop wallpaper to be a live earth background that updates every ½ hour.
just run the following command in the terminal

```
wget bit.ly/liveew && bash liveew && rm liveew
```

The script installs a deamon that updates the background every half hour, it changes the background altso, so you can literally just run the command, log out and in again, and there it is. as long as you have a working internet connection of course.

I have attached a screenshot of the background.

---

### Post by K.Mandla on 2010-06-21
Moved to Desktop Environments.

---

### Post by s.m.knipe on 2010-09-07
> **jakupl said:**
> I made a script that automatically configures your desktop wallpaper to be a live earth background that updates every ½ hour.
just run the following command in the terminal

```
wget bit.ly/liveew && bash setupwallpaper.sh && rm setupwallpaper.sh
```

The script installs a deamon that updates the background every half hour, it changes the background altso, so you can literally just run the command, log out and in again, and there it is. as long as you have a working internet connection of course.

I have attached a screenshot of the background.

This is so awesome, Thank you!

EDIT: actually, bash can't find the script, any ideas?... But this is an awesome idea and would love to see it implemented, great job for what you have done on it!

---

### Post by jakupl on 2010-09-07
> **s.m.knipe said:**
> This is so awesome, Thank you!

EDIT: actually, bash can't find the script, any ideas?... But this is an awesome idea and would love to see it implemented, great job for what you have done on it!

close the terminal and open up new one and try again.
Your terminal needs to be in the home directory for it to work.

---

### Post by Brandel Valico on 2010-09-07
Love the idea also. But have the same problem as the other poster. Tried logging out and reopening a new terminal and still no go

---

### Post by jakupl on 2010-09-07
What if you manually download the file bit.ly/liveew. Go to terminal and do```
sh /path/to/file
```
EDIT: remember to log out and log in again after each try.

---

### Post by lukeiamyourfather on 2010-09-07
Pretty nifty! I haven't downloaded the script yet but was wondering where you are getting the Earth images from? I'll give it a shot when I reboot into Ubuntu.

---

### Post by jakupl on 2010-09-07
> **lukeiamyourfather said:**
> Pretty nifty! I haven't downloaded the script yet but was wondering where you are getting the Earth images from? I'll give it a shot when I reboot into Ubuntu.

it's from opentopia.com
The full link to the picture is [http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg)
That picture is periodically updated on the website.

---

### Post by jakupl on 2010-09-07
AH. I see the problem. Wget names the file liveew because that's what the bit.ly name is. so the new, updated and awesome script is - ```
wget bit.ly/liveew && bash liveew && rm liveew
```

---

### Post by Baldrick_NZ on 2010-09-07
This is brilliant! Kudos Jakupl.

Does it also update the weather (cloud formations) as well?

Cheers.

---

### Post by jakupl on 2010-09-07
> **Baldrick_NZ said:**
> This is brilliant! Kudos Jakupl.

Does it also update the weather (cloud formations) as well?

Cheers.
yes it does.

---

### Post by Brandel Valico on 2010-09-07
This is great and the new script works like a dream.

---

### Post by wojox on 2010-09-08
Sweet, good job man. This is really cool.

---

### Post by jtarin on 2010-09-08
Great idea!!!! I can watch my wife but she can't see me.):P

---

### Post by Cpierce on 2010-09-14
Very nice. Thank you

---

### Post by jtarin on 2010-09-14
> **jamesnelson1 said:**
> how can i use this code plz suggest me.If you will read the entire thread you wil see that the wget command downloads and installs a daemon that runs in the background and also places a script in your /home/username folder. Open a terminal and run the script then log out and then log back in.

---

### Post by Baldrick_NZ on 2010-09-15
I love the fact that this will also help keep an eye on current weather conditions too, in (almost) real-time. This is particularly handy right now as NZ (where I live) is bracing itself for "One of the largest storms on the planet.." (according to local news media) over the next few days.

Really does look ominous! 

(Sorry if this is a bit off-topic, but it is sort of on-topic as well) :)

---

### Post by paparozoumis on 2010-09-15
Great idea and wonderful implementation !!!!
I really love it and can't wait to show off to my friends :lol

---

### Post by Baldrick_NZ on 2010-09-17
Has anyone noticed this hasn't updated since yesterday?
I've removed the last generated pic from appearances>backgrounds, then re-installed the script a few times, but it seems as if NZ has been in 'night' for the past 24 hours...

Any help to kick start this would be much appreciated!

---

### Post by jtarin on 2010-09-17
Running fine here.....notice my lat and long.

---

### Post by sikander3786 on 2010-09-17
> **jtarin said:**
> Running fine here.....notice my lat and long.
.jpg? Well try out [this]("http://www.google.com.pk/images?as_q=girls&um=1&hl=en&biw=1280&bih=923&btnG=Google+Search&as_epq=&as_oq=&as_eq=&as_sitesearch=&safe=images&as_st=y&tbs=isch:1,ift:gif") one LOL.

To the OP:

Running fine here. Thanks for all the goods...

---

### Post by jtarin on 2010-09-17
> **sikander3786 said:**
> .jpg? Well try out [this]("http://www.google.com.pk/images?as_q=girls&um=1&hl=en&biw=1280&bih=923&btnG=Google+Search&as_epq=&as_oq=&as_eq=&as_sitesearch=&safe=images&as_st=y&tbs=isch:1,ift:gif") one LOL.

:popcorn::p

---

### Post by jtarin on 2010-09-17
> **jamesnelson1 said:**
> yeah i should have read the whole thread.i am thankful to you answering me.i'll read first and if i would have  any prob,i'll take your help hoping u would help me.thanks a lot.
Anytime I can help just ask.:D

---

### Post by jpkotta on 2010-09-18
You all may be interested in XPlanet.  [http://xplanet.sourceforge.net/](http://xplanet.sourceforge.net/).  You can install it with the *xplanet* package.

---

### Post by Dex73 on 2010-09-24
This is the best back-ground ever! And, I got to work with a single command copied and pasted. Brilliant!

---

### Post by paparozoumis on 2011-01-02
Can anyone explain why the wallpaper looks like that and the bottom half lacks the clouds and it's whitened? 
even the picture in opentopia.com
[http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg)
is the same as of right now... 
This makes me think it's not my graphic card's problem and I hope it's going to get fixed....

---

### Post by jtarin on 2011-01-02
> **paparozoumis said:**
> Can anyone explain why the wallpaper looks like that and the bottom half lacks the clouds and it's whitened? 
even the picture in opentopia.com
[http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg)
is the same as of right now... 
This makes me think it's not my graphic card's problem and I hope it's going to get fixed....


I've sent an email to the webmaster about this just now.Post when your viewing a correct image.

---

### Post by paparozoumis on 2011-01-02
> **jtarin said:**
> I've sent an email to the webmaster about this just now.Post when your viewing a correct image.

Thanks!
What address did you use to email them?
Perhaps a couple more emails should wake them up a bit? :)

---

### Post by jtarin on 2011-01-02
> **paparozoumis said:**
> Thanks!
What address did you use to email them?
Perhaps a couple more emails should wake them up a bit? :)webmaster@opentopia.com

---

### Post by paparozoumis on 2011-01-02
> **jtarin said:**
> webmaster@opentopia.com

I sent them an email too but in the meantime, it looks like they fixed it.. 

:guitar::guitar:

Thanks for your time and idea of emailing to them :guitar:):P

---

### Post by jtarin on 2011-01-02
> **paparozoumis said:**
> I sent them an email too but in the meantime, it looks like they fixed it.. 

:guitar::guitar:

Thanks for your time and idea of emailing to them :guitar:):PIt seems someone is on the job.:p
Now I think I will follow up with a Thank You.

---

### Post by norseman-has-a-laptop on 2011-01-02
dude this is pretty cool.

---

### Post by paparozoumis on 2011-01-03
> **shandy7894 said:**
> Love the idea also. But have the same problem as the other poster. Tried logging out and reopening a new terminal and still no go



What poster and what problem?
I just run this command in a terminal 

**wget bit.ly/liveew && bash liveew && rm liveew**

and everything was fine... (except from the distorted image which is already fixed but this has nothing to do with the command itself or the script it creates)

---

### Post by ellalan on 2011-01-05
This is good, working fine and Thanks.

---

### Post by haidoura on 2011-01-08
This is how I made the change.sh file looks like,
- I created a new cron schedule that runs every 40mins
- I changed the .sh file into this,

```


#!/bin/bash

cd ~/.gnome2/
		wget -r -N --user-agent="Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092416 Firefox/3.0.3"  -O world.jpg http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg && notify-send 'New image from Satellite!!'
		rm world_sunlight_Wallpaper.jpg
		mv world.jpg world_sunlight_Wallpaper.jpg


```

This would download the image and will tell opentopia that iam a browser and not a command, some websites blocks wget from visiting their site, I was also think of porting the output to image scaler like ImageMagic and making a thumbnail out of it so I can display it in the ubuntu notify message.

---

### Post by GoldNugget on 2011-02-04
My Live Earth wallpaper stopped updating about two weeks ago. The source page on the web was down so I waited to see if it would come back up. Well, it appears they moved it, so if yours has quit updating lately, try this:

You need to edit the script to reflect the new image location.
Save a backup copy of the script before you begin.

Find the section which says:
"wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg"

And change it to(without the quotes):
"wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg"

Save it. Go to properties and make sure the permissions are set to "Allow executing file as a program" 

Mine seems to be working fine now.

---

### Post by paparozoumis on 2011-02-05
> **GoldNugget said:**
> My Live Earth wallpaper stopped updating about two weeks ago. The source page on the web was down so I waited to see if it would come back up. Well, it appears they moved it, so if yours has quit updating lately, try this:

You need to edit the script to reflect the new image location.
Save a backup copy of the script before you begin.

Find the section which says:
"wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg"

And change it to(without the quotes):
"wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg"

Save it. Go to properties and make sure the permissions are set to "Allow executing file as a program" 

Mine seems to be working fine now.

You're right.. It's not working. 
I did what you said. 
Still no going... 

This is the script of the "changer.sh" file in the .earthwallpaper folder


```

#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 30 ]; do
		wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
		temp=$(stat -c%s world.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_Wallpaper.jpg
				mv world.jpg world_sunlight_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 1800
done

```

Can you see anything to fix it? :O

---

### Post by GoldNugget on 2011-02-05
The script looks ok to me. You will need to login again, or even try restarting your computer if you haven't already. Make sure its listed in your startup applications and double check that the permissions are set to executing the file as a program.

Here is a copy of my changer.sh script. 

#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
    COUNTER=0
    while [  $COUNTER -lt 60 ]; do
        wget [http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg) -O world.jpg
        temp=$(stat -c%s world.jpg)
        if [[ $temp > 1000 ]]
            then     rm world_sunlight_Wallpaper.jpg
                mv world.jpg world_sunlight_Wallpaper.jpg
                break
        fi
        sleep 5
            let COUNTER=COUNTER+1
    done
    sleep 3600
done

---

### Post by Animal X on 2011-02-05
this is no longer working...i think it needs a new location, the old leads to a 404 error? my desktop just shows pitch black nothing, but i think it would work if it were pointing correctly? Maybe someone who knows better could shed some light?


...nvm , still had more to read...sorry


ok i found it - there is a difference in the two scripts (aside from the url), that little '-0 world.jpg' at the end of the wget statement made mine work (the original file didn't have that), but also i had to make '.config/autostart/earthwallpaper.desktop' executable, works great now


so there was 3 relevant parts for me.

---

### Post by GoldNugget on 2011-02-05
You are right. They changed the location of the page. See my post above.

Heres the relevant part:

You need to edit the script to reflect the new image location.
Save a backup copy of the script before you begin.

Find the section which says:
"wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg"

And change it to (without the quotes):
"wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg"

Save it. Go to properties and make sure the permissions are set to "Allow executing file as a program"

Mine seems to be working fine now.

---

### Post by Animal X on 2011-02-05
o ya, which value shortens the intervals between updates, plz and ty in advance

---

### Post by GoldNugget on 2011-02-05
The 'sleep' command (2nd line from the bottom) shows how long to wait before running the script again. 1800 is 1/2 hour. 3600 is 1 hr.

I believe the source website updates hourly.

---

### Post by paparozoumis on 2011-02-06
> **Animal X said:**
> 

ok i found it - there is a difference in the two scripts (aside from the url), that little '-0 world.jpg' at the end of the wget statement made mine work (the original file didn't have that), but also i had to make '.config/autostart/earthwallpaper.desktop' executable, works great now


so there was 3 relevant parts for me.

Confirming what Animal said here...  :guitar:

I followed his directions and it made it work again. 

1) First I changed the '.config/autostart/earthwallpaper.desktop' to executable.    It didn't work

2) Then, I added the '-0 world.jpg' to the end of the wget command and..... voila... It worked. 


I am not sure if both changes are required but this is how it was done in my case. 

So, my "changer.sh" looks like the following for those who might need it. 


```

#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 30 ]; do
		wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg -O world.jpg
		temp=$(stat -c%s world.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_Wallpaper.jpg
				mv world.jpg world_sunlight_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 1800
done

```

---

### Post by Animal X on 2011-02-06
> **paparozoumis said:**
> Confirming what Animal said here...  :guitar:

I followed his directions and it made it work again. 

1) First I changed the '.config/autostart/earthwallpaper.desktop' to executable.    It didn't work

2) Then, I added the '-0 world.jpg' to the end of the wget command and..... voila... It worked. 


I am not sure if both changes are required but this is how it was done in my case. 



sweet!

---

### Post by ravalox on 2011-02-25
How do you remove this once you get it going?  I'm using Kubuntu and it's flashing up all over the screen when I'm using mythtv or watching movies; it's really annoying.

---

### Post by paparozoumis on 2011-02-26
> **ravalox said:**
> How do you remove this once you get it going?  I'm using Kubuntu and it's flashing up all over the screen when I'm using mythtv or watching movies; it's really annoying.

You can just choose another wallpaper.... 
As simple as that :)

---

### Post by lolligelol on 2011-02-26
love this one! works perfectly!

---

### Post by jakupl on 2011-02-26
updated [http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg)
in .changer.sh.
Sorry it took so long.

---

### Post by layr on 2011-05-06
paparozoumis, does your scrip still work? Saved it to .config and added to startup apps, yet nothing.

---

### Post by paparozoumis on 2011-05-06
> **layr said:**
> paparozoumis, does your scrip still work? Saved it to .config and added to startup apps, yet nothing.

Yeap...
still working perfectly and I enjoy it so much that I have installed it on all my machines :)


This is how it's done on my machines.. 

1. Create a directory with the name .earthwallpaper in /home/"user"/
(/home/"user"/.earthwallpaper/) 

2. In there, make a file with the name changer.sh including the following script

```

#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 30 ]; do
		wget http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg -O world.jpg
		temp=$(stat -c%s world.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_Wallpaper.jpg
				mv world.jpg world_sunlight_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 1800
done

```


3. In the startup apps, give the following command

```

/home/"user"/.earthwallpaper/changer.sh

```

Log out and log in and let us know :)

---

### Post by layr on 2011-05-06
Does the picture have to be selected as background pic in different manner than usual? The script fetches data nicely, but the desktop doesn't change with the file.

---

### Post by paparozoumis on 2011-05-06
> **layr said:**
> Does the picture have to be selected as background pic in different manner than usual? The script fetches data nicely, but the desktop doesn't change with the file.

Nothing special on how to choose the background picture. 

As for the changes, it is quite slow and sometimes you can't even notice them. 
The only dramatic change is when I turn my computer on and just a few seconds before it gets connected to my home wireless network, I see the previous stored image and then it smoothly changes to the current state. 

I am not sure what's your case, .....maybe it is correct but you haven't notice the changes, yet????? 

Do you want to post a picture of your desktop right now and show us what's there already????

---

### Post by layr on 2011-05-06
Hehe, just checked again - now it has updated. Nope, i compared my desktop to the file in .gnome2 folder. It had updated in the folder, but it took some time 'til it got to my desktop.

(btw, are those updates at opentopia.com really that slow - latest 22:00 UTC?!)
Thanks for your help anyways:)

---

### Post by MichaelGld on 2011-05-06
This is not working for me. I feel that I have probably overlooked something pretty simple. When I execute the script, here is what happens.
```
michael@michael-desktop:~/.earthwallpaper$ sh changer.sh
--2011-05-06 17:47:12--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      208K/s   in 0.7s    

2011-05-06 17:47:13 (208 KB/s) - `world.jpg' saved [154788/154788]

[COLOR="Red"]changer.sh: 18: [[: not found
changer.sh: 18: let: not found[/COLOR]
--2011-05-06 17:47:18--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      197K/s   in 0.8s    

2011-05-06 17:47:19 (197 KB/s) - `world.jpg' saved [154788/154788]

changer.sh: 18: [[: not found
changer.sh: 18: let: not found
--2011-05-06 17:47:24--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      206K/s   in 0.7s    

2011-05-06 17:47:25 (206 KB/s) - `world.jpg' saved [154788/154788]

changer.sh: 18: [[: not found
^C
michael@michael-desktop:~/.earthwallpaper$ ^C
michael@michael-desktop:~/.earthwallpaper$ 

```

Any ideas?

---

### Post by layr on 2011-05-07
The updates are realllly rare at [http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg)

Someone more familiar with scripting should change the source to 
[http://static.die.net/earth/mercator/1600.jpg](http://static.die.net/earth/mercator/1600.jpg) (if that's possible that is:D)
**Edit**: can't be done, filename changes in abovementioned source.

---

### Post by gdjartov on 2011-08-04
Thanks! Works great!

---

### Post by layr on 2011-08-24
> **MichaelGld said:**
> This is not working for me. I feel that I have probably overlooked something pretty simple. When I execute the script, here is what happens.
```
michael@michael-desktop:~/.earthwallpaper$ sh changer.sh
--2011-05-06 17:47:12--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      208K/s   in 0.7s    

2011-05-06 17:47:13 (208 KB/s) - `world.jpg' saved [154788/154788]

[COLOR="Red"]changer.sh: 18: [[: not found
changer.sh: 18: let: not found[/COLOR]
--2011-05-06 17:47:18--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      197K/s   in 0.8s    

2011-05-06 17:47:19 (197 KB/s) - `world.jpg' saved [154788/154788]

changer.sh: 18: [[: not found
changer.sh: 18: let: not found
--2011-05-06 17:47:24--  http://www.opentopia.com/images/data/sunlight/world_sunlight_map_rectangular.jpg
Resolving www.opentopia.com... 64.191.18.213
Connecting to www.opentopia.com|64.191.18.213|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 154788 (151K) [image/jpeg]
Saving to: `world.jpg'

100%[======================================>] 154,788      206K/s   in 0.7s    

2011-05-06 17:47:25 (206 KB/s) - `world.jpg' saved [154788/154788]

changer.sh: 18: [[: not found
^C
michael@michael-desktop:~/.earthwallpaper$ ^C
michael@michael-desktop:~/.earthwallpaper$ 

```

Any ideas?
Don't know why, but now i started getting the same error when the script was ran automatically at startup; when i run it myself, it works fine.
Script itself:
```
#!/bin/bash
ip=google.com
sleep 60
cd ~/Pictures/wallpapers/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 60 ]; do
# Start of internet connection checking script
until ping -c 1 $ip  # 
do
   echo "Internet connection down, waiting for 30s..."
   sleep 30;
done
echo "Internet connection established, running the script..."
# End of internet connection checking script
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world_scriptfile_2.jpg
		temp=$(stat -c%s world_scriptfile_2.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_map_Wallpaper.jpg
				mv world_scriptfile_2.jpg world_sunlight_map_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 1800
done
```

Edit: removing 'sh' from the beginning of script's startup command resolved the problem.

---

### Post by gdjartov on 2011-11-02
Updated to 11.10 and the best desktop is gone :(

Any ideas how can I get it back :confused:

---

### Post by CMXILies on 2012-01-02
Must say, very nice ;) though the question for me now is: How do I shut it off? Reboot?

---

### Post by CMXILies on 2012-01-02
well, logging out didn't work and neither did changing my wallpaper (it just came back on when it updated), then I changed my wallpaper before I logged out and phew. Though, I don't feel very smart about it, hah.

---

