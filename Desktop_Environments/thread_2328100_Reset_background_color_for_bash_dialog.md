---
title: "Reset background color for bash dialog?"
date: 2016-06-17
forum: Desktop Environments
---

### Post by CrewDK on 2016-06-17
Hey. 

I got some script where i'm useing dialog command. 

```
#!/bin/bash

tmpfile=$(mktemp tmp.XXXXXXX --tmpdir=/tmp 2>/dev/null) || tmpfile=/tmp/test$$

dialog          --backtitle "&#1050;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1072;"  \
                --title "&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072;" \
                --clear \
                --checklist "&#1057;&#1087;&#1080;&#1089;&#1086;&#1082; &#1079;&#1072;&#1076;&#1072;&#1085;&#1080;&#1081;" 15 50 4 \
                1 "Install LAMP" on \
                2 "Setup IPTABLES" on 2> ${tmpfile}

if [ "$?" -eq "0" ]; then

grep -o 1 $tmpfile > /dev/null 2>&1
    if [ "$?" -eq "0" ]; then
    echo 123
    fi


grep -o 2 $tmpfile > /dev/null 2>&1
    if [ "$?" -eq "0" ]; then
    echo 123
    fi

else

    echo "Interrupted"

fi

```

Is there any way to reset background and font colours back to default black\white after filling dialog "form"? I tried to use "clear" but it's no use. :(

---

### Post by Habitual on 2016-06-17
Background color of the dialog or the terminal after the dialog/script exits?
And running your script, selections are both pre-filled. Both chosen.

---

### Post by CrewDK on 2016-06-17
I'm talking about blue BG color. For example, i want to see some output after running dialog and this blue BG a little bit noisy :(
Is there any way after close dialog form itself reset this colours back to default?

---

### Post by Skaperen on 2016-06-18
what did the *clear* command do?  the *dialog* man page says that is what to do.  maybe your terminal was not set to the default colors.  try *clear* by itself and tell us what happens.  what terminal are you running?  maybe *setterm* can do what you need.

---

### Post by Habitual on 2016-06-19
clear or reset command.

---

### Post by CrewDK on 2016-06-19
Yeah. I know about clear, but some strange way when I run this script in ssh session it looks for me like this. If i run this script in real terminal - all works just fine. So what wrong with ssh session or what?

---

### Post by CrewDK on 2016-06-19
> **Skaperen said:**
> what terminal are you running?  maybe *setterm* can do what you need.

How can I check what terminal i'm running? Sorry i'm still not so good with linux :) Are you talking about that? 

[SIZE=4][IMG]http://crewdk.ru/fscapture/2016-06-20_062634.jpg[/IMG][/SIZE]

I tried use setterm with --default and --reset but this didn't helped me :(

---

### Post by Skaperen on 2016-06-19
it look like you are running putty.  maybe it is emulating a terminal wrong.  install ubuntu (in a virtual machine) and use that

---

### Post by CrewDK on 2016-06-20
I'm running "Xshell". This is too ssh client for windows PCs. And as I already told - when I'm running this script  in "real" terminal (yeah, on virtual machine) - all works fine. So maybe some one have any idea what setting for ssh client I should look for?

---

### Post by Skaperen on 2016-06-24
welcome to the world of "compatibility" with Windows stuff.

---

