---
title: "Cron bash script using ifconfig wont display"
date: 2012-01-30
forum: Desktop Environments
---

### Post by juliushibert63 on 2012-01-30
I have a remote machine that occasionally changes IP locally and/or public IP to. I have DYNDNS setup as well to help combat this. 

However I've written a small script that emails me my IP both local and public IPs setup as a cron job to run every 15 mins. The script works perfectly when run in a terminal window when I'm logged in either at the computer or via SSH. However as soon as the script is run as a cron job it only displays the public IP and not the local IP. It's almost as though ifconfig isn't working when run by cron.

Any ideas?


```
#!/bin/bash


# Email variables for Sendemail

#set -xv

# Email details
TO="*****"
FROM="*****"
SUBJECT="Current IP is "
MESSAGE_BODY=" "

# SMTP server details
SMTP_SERVER="******"
SMTP_USER="*****"
SMTP_PWD="*****"
SMTP_PORT="465"


send_email() 
{
EMAIL_SUBJECT="${1}"
EMAIL_MESSAGE="${2}"

	sendemail -f $FROM -t $TO -u "${EMAIL_SUBJECT}" -m "${EMAIL_MESSAGE}" -s $SMTP_SERVER -o tls=yes -xu $SMTP_USER -xp $SMTP_PWD 
	return 0
}


MESSAGE_BODY=`echo -e "\nExternal IP: "`
MESSAGE_BODY="${MESSAGE_BODY} `wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`"
MESSAGE_BODY="${MESSAGE_BODY} `echo -e "\n\nInternal IP: "`"
MESSAGE_BODY="${MESSAGE_BODY} `ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1 }'`"
MESSAGE_BODY="${MESSAGE_BODY} `echo -e "\n\n "`"
MESSAGE_BODY="${MESSAGE_BODY} `ifconfig`"


SUBJECT="${SUBJECT} (`wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`)"


send_email "${SUBJECT}" "${MESSAGE_BODY}" # send email 

exit 0

```

---

### Post by amauk on 2012-01-30
ifconfig is in /sbin/
By default, cron's path doesn't include /sbin

Use the full path to ifconfig

```
#!/bin/bash


# Email variables for Sendemail

#set -xv

# Email details
TO="*****"
FROM="*****"
SUBJECT="Current IP is "
MESSAGE_BODY=" "

# SMTP server details
SMTP_SERVER="******"
SMTP_USER="*****"
SMTP_PWD="*****"
SMTP_PORT="465"


send_email() 
{
EMAIL_SUBJECT="${1}"
EMAIL_MESSAGE="${2}"

	sendemail -f $FROM -t $TO -u "${EMAIL_SUBJECT}" -m "${EMAIL_MESSAGE}" -s $SMTP_SERVER -o tls=yes -xu $SMTP_USER -xp $SMTP_PWD 
	return 0
}


MESSAGE_BODY=`echo -e "\nExternal IP: "`
MESSAGE_BODY="${MESSAGE_BODY} `wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`"
MESSAGE_BODY="${MESSAGE_BODY} `echo -e "\n\nInternal IP: "`"
MESSAGE_BODY="${MESSAGE_BODY} `[COLOR="Red"]/sbin/ifconfig[/COLOR] | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1 }'`"
MESSAGE_BODY="${MESSAGE_BODY} `echo -e "\n\n "`"
MESSAGE_BODY="${MESSAGE_BODY} `[COLOR="Red"]/sbin/ifconfig[/COLOR]`"


SUBJECT="${SUBJECT} (`wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`)"


send_email "${SUBJECT}" "${MESSAGE_BODY}" # send email 

exit 0

```

---

### Post by juliushibert63 on 2012-01-30
amauk: thank you!

---

### Post by juliushibert63 on 2012-01-30
Actually is there anyway of being able to run the job as cron via SSH so I can check it is working correctly?

---

