---
title: "Conky"
date: 2009-06-02
forum: General Help
---

### Post by tcpa41 on 2009-06-02
Hello, and sorry  if  I am posting not in the right section. Today while trying to make audacious date show up in conky i stumbled upon a problem,when conky launches it spams me that variables i used to retrieve audacious are uknown-but i took them from official conky documentation variable list. How do you think,what may be the problem,or maybe data from audacious can be retrieved in another way? :popcorn:

BTW Here's code:
```
${color white}NOW PLAYING ${hr 1}${color}
PL.Status: $alingr$audacious_status
Songname: $alignr$audacious_title
Bitrate: $alignr$audacious_bitrate
Song At: $alignr$audacious_position
Volume: $alignr$audacious_main_volume
```

---

### Post by Tibuda on 2009-06-02
type **conky -v** in your terminal, and see if your conky have the audacious music detection enabled.

---

### Post by Sarai the Geek on 2009-06-02
> **tcpa41 said:**
> Hello, and sorry  if  I am posting not in the right section. Today while trying to make audacious date show up in conky i stumbled upon a problem,when conky launches it spams me that variables i used to retrieve audacious are uknown-but i took them from official conky documentation variable list. How do you think,what may be the problem,or maybe data from audacious can be retrieved in another way? :popcorn:

BTW Here's code:
```
${color white}NOW PLAYING ${hr 1}${color}
PL.Status: $alingr$audacious_status
Songname: $alignr$audacious_title
Bitrate: $alignr$audacious_bitrate
Song At: $alignr$audacious_position
Volume: $alignr$audacious_main_volume
```

I'm not sure if this is required for proper functioning (if it is, it could be your problem) but I find it's easier to read my .conkyrc when I use curly brackets, like myeh:
```
${color white}NOW PLAYING ${hr 1}${color}
PL.Status: ${alingr}${audacious_status}
Songname: ${alignr}${audacious_title}
Bitrate: ${alignr}${audacious_bitrate}
Song At: ${alignr}${audacious_position}
Volume: ${alignr}${audacious_main_volume}
```

Just a thought. : )

---

### Post by tcpa41 on 2009-06-02
> **danielrmt said:**
> type **conky -v** in your terminal, and see if your conky have the audacious music detection enabled.

I jus checked it out,and it said in music detection,that only mdp is enabled,does that mean that i will need to manually compile conky in order to make audacious detection working?

---

### Post by Tibuda on 2009-06-02
See this thread: [http://ubuntuforums.org/showthread.php?t=411010&page=2](http://ubuntuforums.org/showthread.php?t=411010&page=2)
The guy uses another way to display the data

---

