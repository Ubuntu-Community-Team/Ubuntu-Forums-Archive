---
title: "Skype and Skysentials with a single icon"
date: 2007-10-01
forum: Desktop Environments
---

### Post by Martin on 2007-10-01
Hi,
 
I'm using the Skysentials GUI to send SMS from Skype within Gutsy and it works great. I've got a desktop icon for Skype and and one for Skysentials. 
In order for Skysentials to work Skype has to be up and running.
Does anybody know how I could combine the 2 under a single launcher so that Skype is launched and then  maybe 20 seconds later Skysentials is kicked-off?

---

### Post by MrFSL on 2007-10-06
There are a lot of ways that you can do this:

You could write a bash script that opens skype, waits 20 seconds and then runs skysentials:
```
#!/bin/bash

/path/to/skype

sleep 20

/path/to/skysentials.py
```

Of course this is a bit crude. What happens if skype is already running? Then you have to wait for nothing. My suggestion is a script that first checks if skype is running. If yes then run skysentials. If not then load skype, check that it's running, and then run skysential.

```
#!/usr/bin/perl

# Enter Path To Applications
$skype_path = "/usr/bin/skype";
$skysentials_path = "/home/fsl/Desktop/skysentials-1.0.0/skysentials.py";

# Get UID of current user
$who_r_you = $<;

# See if skype is running
$skype_running = grep /skype/, `ps -U $who_r_you -u $who_r_you`;

# If Skype is running start Skysentials
if ("$skype_running" eq "1") { 
	`$skysentials_path`;

# Else start Skype and wait for it to start before starting sSkysentials
} else {
	open(SKYPE, "$skype_path 2>\&1 |");
	while (<SKYPE>) {
		$double_check = grep /skype/, `ps -U $who_r_you -u $who_r_you`;
		if ("$double_check" eq "1") {
			`$skysentials_path`;
			exit;
		} else {
			sleep 1;
		}
	}
}
```
Of course you will have to change these two lines:```
$skype_path = "/usr/bin/skype";
$skysentials_path = "/home/fsl/Desktop/skysentials-1.0.0/skysentials.py";
``` to reflect your system.

---

### Post by Martin on 2007-10-11
Nice!

I was going down the bash route but was running into precisely the problem you pointed out - what happens if Skype is already running?
Lacking the skills to make further progress I posted the original question. Thanks for the response.

---

### Post by MrFSL on 2007-10-12
My pleasure. I take it that it worked as expected for you?
:)

---

### Post by eekfonky on 2008-05-12
How do you create a script and where do you save it once it's written to make it executable?

---

