---
title: "Send email from bash using GMail's stmp server."
date: 2010-05-04
forum: Desktop Environments
---

### Post by cipherboy_loc on 2010-05-04
Is there a way to send an email from the terminal using the GMail stmp server? I want to be able to run a script that will generate /tmp/email.txt (which will contain information about my public ip address, my private ip address, make sure vnc and ssh are running, among other things like making sure I can connect to the internet) and send it to my GMail account. I have tried using sendEmail using the instructions located [here]("http://www.debianadmin.com/how-to-sendemail-from-the-command-line-using-a-gmail-account-and-others.html"), but I receive this error: 

cipherboy@cipherboy-workstation:~$ cat /tmp/email.txt | sendEmail -f [email]xxxxxxxx.xx@gmail.com[/email] -t [email]xxxxxxxx.xx@gmail.com[/email] -u "Status Update" -s stmp.gmail.com -o tls=yes -xu [email]xxxxxxxx.xx@gmail.com[/email] -xp <password removed for security issues> -o message-file=/tmp/email.txt
May 04 11:15:07 cipherboy-workstation sendEmail[4110]: ERROR => Connection attempt to stmp.gmail.com:25 failed: IO::Socket::INET: connect: Connection timed out


I have tried replacing -o tls=yes with -o ssl=yes because I have evolution set up to use ssl with my GMail account.


Thanks in advance,

The Lord of Ciphers,
Cipherboy

---

### Post by DZ* on 2010-05-04
Looks like it connects to a wrong port (25). I'm not familiar with sendEmail, but you could do that with msmtp
(sudo apt-get install msmtp openssl ca-certificates)
Put this in ~/.msmtprc :
```
account default
host smtp.gmail.com
port 587
from me@gmail.com
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on
user me@gmail.com
password gmailpassword
logfile ~/.msmtp
```

msmtp -t < somefile
First lines of 'somefile' should be header info such as To:, From:, Subject:.

---

### Post by cipherboy_loc on 2010-05-04
Thanks, it worked!

---

### Post by lisati on 2010-05-04
Possible typo: it's usually smtp, not stmp.

---

### Post by magnums on 2012-07-15
I want to send by including with a attach file. 
How to do that?

Thank in advance.

---

### Post by hakermania on 2012-07-15
> **magnums said:**
> I want to send by including with a attach file. 
How to do that?

Thank in advance.

Please start a new thread for such questions, and let such old threads to die.

Here's the send.py python script:
```

#!/usr/bin/python
import os, re
import sys
import smtplib
 
#from email.mime.image import MIMEImage
from email import encoders
from email.mime.multipart import MIMEMultipart
from email.mime.base import MIMEBase
from email.MIMEText import MIMEText

 
SMTP_SERVER = 'smtp.gmail.com'
SMTP_PORT = 587

 
sender = 'myemail@gmail.com'
password = "mypass"
recipient = sys.argv[1]
subject = ''
message = sys.argv[3]
 
def main():
    msg = MIMEMultipart()
    msg['Subject'] = sys.argv[2]
    msg['To'] = recipient
    msg['From'] = sender
    
    
    part = MIMEText('text', "plain")
    part.set_payload(message)
    msg.attach(part)
    
    session = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)
 
    session.ehlo()
    session.starttls()
    session.ehlo
    
    session.login(sender, password)

    fp = open(sys.argv[4], 'rb')
    msgq = MIMEBase('audio', 'audio')
    msgq.set_payload(fp.read())
    fp.close()
    # Encode the payload using Base64
    encoders.encode_base64(msgq)
    # Set the filename parameter
    filename=sys.argv[4]
    msgq.add_header('Content-Disposition', 'attachment', filename=filename)
    msg.attach(msgq)
    # Now send or store the message
    qwertyuiop = msg.as_string()



    session.sendmail(sender, recipient, qwertyuiop)
    
    session.quit()
    os.system('notify-send "Email sent"')
 
if __name__ == '__main__':
    main()

```
It is used as:
```

python send.py "receiver@gmail.com" "My Topic" "My text" "My attachment.jpg"

```
You may sent anything that gmail permits!
Edit the first lines:
```

sender = 'myemail@gmail.com'
password = "mypass"

```
and be **very** careful with this file, it contains your password in plain text. Either way, you can make the script to accept your password as argument, but then, remember to delete the entry from the ~/.bash_history (and NOT with gedit, he will let a ~/.bash_history~ file back with your password, unless you've told him not to)

---

### Post by magnums on 2012-07-15
[@hakermania]("http://ubuntuforums.org/member.php?u=895189")
Yess,   It's work now.!!!
Thank you Very Much.

---

### Post by hakermania on 2012-07-15
> **magnums said:**
> [@hakermania]("http://ubuntuforums.org/member.php?u=895189")
Yess,   It's work now.!!!
Thank you Very Much.

You are welcome. If you install libnotify-bin
```

sudo apt-get install libnotify-bin

```
it will also show a pop-up message each time an email has been successfully sent.

---

