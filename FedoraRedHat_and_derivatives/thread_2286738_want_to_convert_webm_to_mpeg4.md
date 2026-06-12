---
title: "want to convert webm to mpeg4"
date: 2015-07-14
forum: Fedora/RedHat and derivatives
---

### Post by thomas52 on 2015-07-14
[HR][/HR] 			 		  		 		 			     		      hi friends.
  i want to convert webm files  into mpeg4 can you please and good free and open source converters ?  that i can use in fedora 22. can you also please tell me how to install  them using the  regular dnf command.?
thanks.

---

### Post by TheFu on 2015-07-14
The basic form is:```

$ ffmpeg -i input.webm output.mp4
```

You might want to use a preset to better control the time/quality.```

$ ffmpeg -i input.webm -vcodec libx264 -crf 19.5 -preset medium -strict experimental -c:a aac output.mp4
```

Just need an ffmpeg that supports webm - think that was added last year, so it shouldn't be hard.

Don't know how to install anything on fedora, sorry. Doesn't yum work?

---

### Post by QDR06VV9 on 2015-07-14
> **TheFu said:**
> The basic form is:```

$ ffmpeg -i input.webm output.mp4
```

You might want to use a preset to better control the time/quality.```

$ ffmpeg -i input.webm -vcodec libx264 -crf 19.5 -preset medium -strict experimental -c:a aac output.mp4
```

Just need an ffmpeg that supports webm - think that was added last year, so it shouldn't be hard.

Don't know how to install anything on fedora, sorry. _Doesn't yum work?_
yum warns to use dnf instead.
Example
> # dnf install your package here
Fedy lets you install multimedia codecs and additional software that Fedora [doesn't want to ship]("https://fedoraproject.org/wiki/Forbidden_items?rd=ForbiddenItems"), like mp3 support, Adobe Flash, Oracle Java etc., and much more with just a few clicks.
                      To install Fedy in Fedora, open a Terminal and run the following command,
```
                         su -c "curl [https://satya164.github.io/fedy/fedy-installer](https://satya164.github.io/fedy/fedy-installer) -o fedy-installer && chmod +x fedy-installer && ./fedy-installer"                     


```
More on Fedy packages [https://fedoraproject.org/wiki/Forbidden_items?rd=ForbiddenItems](https://fedoraproject.org/wiki/Forbidden_items?rd=ForbiddenItems)
[h=1][SIZE=2]Getting ffmpeg to work with libfaac on Fedora [/SIZE][/h]
[http://www.itbh.at/getting-ffmpeg-to-work-with-libfaac-on-fedora-21-to-be-able-to-stream-a-video-to-a-chromecast-device/?lang=en](http://www.itbh.at/getting-ffmpeg-to-work-with-libfaac-on-fedora-21-to-be-able-to-stream-a-video-to-a-chromecast-device/?lang=en)

Cheers

---

### Post by thomas52 on 2015-07-15
no sir yum command doesn't work now its has been replaced with _**dnf**_

---

### Post by TheFu on 2015-07-15
So with the instructions above and my example commands, this is solved. Right?

---

