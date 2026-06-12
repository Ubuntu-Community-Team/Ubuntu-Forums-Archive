---
title: "Improving Automatix"
date: 2006-02-05
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-05
Please forgive me if I have posted this in the wrong section, the plethora of Automatix posts is a bit mind boggling. That said, I believe I have an idea which would improve Automatix.

Let's face it, newbies are intimidated by the command line and a gui will be more widely accepted than typing out commands in cli. This, I believe, is Microsoft's fault for turning their users into idiots, but I digress.

Hypothetical situation: I use Automatix to install Gnomebaker. Then at a later date, I want to uninstall Gnomebaker.

Automatix starts up with a list of checkboxes that the user can check in order to install desired software. These checkboxes are, by default, empty allowing the user to check the individual software to be installed.

The lines in Automatix which are responsible for installing Gnomebaker are:

```

	FALSE	$"Gnomebaker"		$"The best GTK2 cd/dvd burning software" \

```
This line is responsible for presenting the user with a checkbox for gnomebaker to allow the user to check if they desire gnomebaker to be installed, or leave empty if they don't want gnomebaker.

This line:
```

	if echo "$RET" | grep $"Gnomebaker"; then
		gnomebaker
	fi

```
returns, to Automatix, whether or not the user has checked the box to install Gnomebaker.

Then Automatix uses these lines to proceed with installing Gnomebaker **if** the user chose to install it:

```

function gnomebaker {
	# Install Gnomebaker
	zenity --progress --pulsate --title "Automatix" --text $"Installing Gnomebaker" & 
	ZENITY_PID="$!"
	sudo apt-get --assume-yes install gnomebaker && kill -9 $ZENITY_PID
	
}

```

My idea is this: How about having Automatix install a logfile such as /path/to/logfile and have that file contain a list of software Automatix can process, something like:

```

somesoftware1    <-- the "1" meaning that Automatix has installed this
gnomebaker1    <-- the "1" meaning that Automatix has installed this
somesoftware0    <-- the "0" meaning that Automatix has not installed this

```

Then, have Automatix do:
```

if /path/to/logfile | grep "gnomebaker1";
	then TRUE	$"Gnomebaker"		$"The best GTK2 cd/dvd burning software" \
else
	then FALSE	$"Gnomebaker"		$"The best GTK2 cd/dvd burning software" \
fi

```
in the "function choose" section of Automatix. This would show the state of the gnomebaker installation the last time Automatix was completed.

Then, if the user wants to uninstall gnomebaker:
```

if echo "$RET" | grep $"Gnomebaker"; then
	gnomebaker
else
	gnomebaker0
fi

```
If the user chooses to uninstall gnomebaker:
```

function gnomebaker0 {
	# uninstall Gnomebaker
	zenity --progress --pulsate --title "Automatix" --text $"Installing Gnomebaker" & 
	ZENITY_PID="$!"
	sudo dpkg --purge gnomebaker && kill -9 $ZENITY_PID
	# update the logfile
	sed -ie 's/gnomebaker1/gnomebaker0/g' /path/to/logfile
}

```


If the user has used Automatix to uninstall gnomebaker and wants to reinstall it:
```

function gnomebaker {
	# Install Gnomebaker
	zenity --progress --pulsate --title "Automatix" --text $"Installing Gnomebaker" & 
	ZENITY_PID="$!"
	sudo apt-get --assume-yes install gnomebaker && kill -9 $ZENITY_PID
	# update the logfile
	sed -ie 's/gnomebaker0/gnomebaker1/g' /path/to/logfile
}

```

Of course, all of this will add to the codebase of Automatix and bring in another dependency, sed, but I feel that the work is worth the outcome.

I don't use Automatix nor am I an expert on it, nor am I an expert of bash but I am learning. However, I hope that I have made this clear enough so that people can understand it. This post is being made for the sole purpose of improving Automatix and I want arnieboy to know that I appreciate all of his hard work :)

---

### Post by BLTicklemonster on 2006-02-06
Great idea. Did you try PMing Arnieboy with this?

---

### Post by ardchoille on 2006-02-06
D'oh! No, I didn't think of using the PM system at all. Thanks for the heads up :)

EDIT: PM sent :)

---

### Post by ardchoille on 2006-02-06
I have spoken with arnieboy and he did a very good job of explaining why my idea would not work.

Suppose the user ran Automatix a second time and chose to uninstall one app. When the user pressed the OK button, all of the apps that are checked (the ones which were installed the first time Automatix was run) will be installed all over again since those checkboxes are checked. Also, the checkboxes which were unchecked when the user ran Automatix a second time, those will be unchecked when the user presses the OK button and Automatix will try to uninstall those.. but they weren't installed to begin with.

We need to find a way for Automatix to tell the difference between which checkboxes are checked and which aren't and process those differences when the user presses the OK button so that Automatix won't try to uninstall apps which aren't installed.

I wish I was good with python, I'd port Automatix to python and have better control of this.

Oh well, thank you arnieboy for your explanation and helping me to understand Automatix a bit better.

---

