---
title: "inspiron 4700 , moniter cannot display this video mode"
date: 2009-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shpongle on 2009-05-31
hey , i installed mint on my cousins pc a dell inspiron 4700, and i had to install in safe mode coz an error kept saying cannot display this video mode kept coming up, so i installed it and all went well, but then when i restarted the same thing kept happening, the install works fine coz iv checked it on my monitor and then plugged in the other one (dell) and its worked fine till a restart , is there a way i can set mint to boot up in safe mode? or edit a file to store the settings to run on the monitor, thanks

---

### Post by Shpongle on 2009-05-31
any ideas?

---

### Post by philcamlin on 2009-05-31
had the same issue on a GX280 

i just messed around with the settings on my pc and monitor i cant remember what i did but tinker with it :popcorn:

---

### Post by Shpongle on 2009-05-31
yea il keep at it, retrying jaunty on it now!, its just that mint would have been easier for my cousins

---

### Post by unutbu on 2009-05-31
Perhaps take a look this post: [http://ubuntuforums.org/showpost.php?p=7244593&postcount=4](http://ubuntuforums.org/showpost.php?p=7244593&postcount=4)

What is the make/model of your cousin's monitor?
Do you have the manual? In the back of the manual they usually have a specifications table which lists the horizontal sync range (in KHz) and the vertical refresh rate (in Hz).

For example, these numbers work for a Dell M780:
```

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 30-85
	VertRefresh 50-160
EndSection
```

If you do not have the manual or can not find the right numbers, perhaps do a Google search, or post it and I'll see if I can find it.

---

### Post by Shpongle on 2009-05-31
thanks for the help man , but i got it all set up and running under jaunty now so, as long as my cousins can use it it'll be grand!,

---

