---
title: "Whiptail inputbox help"
date: 2009-02-14
forum: General Help
---

### Post by homemadejam on 2009-02-14
I am trying to create a very simple interface using Whiptail.
I need the user to input their username, so I have:

```
whiptail --inputbox "Username:" 30 100
```

I now want to store what ever the user enters to $user

Can anyone help me with this?

thanks in advice,

Jam

---

### Post by RHTopics on 2009-02-15
Here is an example script for your consideration:

```
#!/bin/bash
#    name: input_name.sh
# created: 02/15/2009

user_name=$HOME/user_name.txt

whiptail --backtitle "A Simple User Interface" \
         --inputbox "User Name:" 10 20 \
         2> "$user_name"

if [ $? = 0 ]; then
    echo "The user name is "`cat "$user_name"`
else
    rm -f "$user_name"
    echo "Canceled."
fi

exit 0

```

---

### Post by homemadejam on 2009-02-15
Ah that is exactaly what I needed!
Thanks a lot for your help :)

Jam

---

