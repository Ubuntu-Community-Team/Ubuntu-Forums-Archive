---
title: "Help: need to grab event: &quot;connected in my lan so start the damn script&quot;!!"
date: 2009-03-11
forum: General Help
---

### Post by h4p0 on 2009-03-11
Hi!
I've a question for you,
I must **automatically** sync two machines in my Lan (desktop & laptop).
I wouldn't use crontab because of polling ( it will try and try forever even if i connect my pc @ work or in any other place )
is there any **other** way to execute a script
**ONLY when I connect the laptop to MY Lan**?????

It would be a thing like:
```

onEVENT(connected@home){  // not CRON!:(
if(MYserver_is_up){ //ping?nmap???
start_sync_script(); //or any other action 
}
}

```

I don't know if I got it across.:P

---

### Post by gersongarcia on 2009-03-11
Dear h4p0,

If I understand your problem, you want to write a daemon that checks if your laptop is connected and if it is you want to execute some script to synch your data, is that correct?

This is something you can try:

# cat chketh0.sh
while [ TRUE ]
do

        getstatus=`ifconfig eth0 | grep "UP BROADCAST RUNNING"`

        if [ "$getstatus" != "" ]
        then

                echo "Interface eth0 up!"
        else
                echo "Interface eth0 down!"

        fi


        sleep 5
done
# ./chketh0.sh
Interface eth0 up!
Interface eth0 up!

---

### Post by h4p0 on 2009-03-13
Cron is better of a "while(true)-sleep" combo :)
I prefer to know if exist a EVENT GRABBER or, for example, a group of script that already starts when I plug the cable, so I can add my instruction(s) within.
regards

---

