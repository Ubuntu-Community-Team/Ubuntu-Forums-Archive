---
title: "Custom  terminal header"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by jsullivan on 2008-04-02
I've been thinking... The kernel headers supplied with a Ubuntu are just boring, so i was wondering about  users making a list of your customized headers from  the .bashrc file.

To start heres mine :

```
     
PS1='\n[\[\e[36;40m\]\u \t \e[0m\]] \[\e[0;31;40m\]\W \[\e[0m\]\$                          
```

To make it a bit more flashy I added this l to mine 

```

#---------------------------------------------------------------------------
#------WELCOME MESSAGE-------------------------------------------
# this will display the username, date, time, a calendar, 
# the amount of users, and the up time and a random fortune.
clear
/usr/games/fortune
echo -e ""
echo -ne "Today is "; date
echo -e ""; cal ;
echo -ne "Up time:";uptime | awk /'up/
{print $3,$4}'
echo "";

```

---

