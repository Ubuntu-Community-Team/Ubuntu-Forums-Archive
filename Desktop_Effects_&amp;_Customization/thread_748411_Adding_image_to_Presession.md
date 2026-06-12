---
title: "Adding image to Presession"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by DemiAlbedo on 2008-04-07
I have been going all out tweaking and editing my desktop however I have become stumped on one topic. I have edited my boot splash but I am running into a problem. Just after you log in there is a tan screen, my boot splash, then back to the tan screen. then the desktop will load. The boot splash does not have a nice transition because it is started with a tan screen then finished with a tan screen. I have found how to change the tan screen to another colour under /etc/gdm/PreSession/Default, however I was wondering if anyone has figured out how to add an image in the PreSession. If i am able to add my boot splash image to the Presession then that would make a perfect transition. 

# **Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image** 
		BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""

It says you can change the background type to "3" for image. . .however where do you insert the image so that it will load it on startup. . .is this the right section to do something like that?

Thanks for the help in advance

---

