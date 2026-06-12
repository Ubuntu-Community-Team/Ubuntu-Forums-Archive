---
title: "Script help please"
date: 2009-04-11
forum: General Help
---

### Post by Blackdragon1400 on 2009-04-11
could someone check my syntax because this will not seem to work, i cant execute any command after the if statement from the then statement. I'm writing this on my desktop but its on my laptop so I'm going to append it with some comments so i dont have to write all of the text, it will be obvious...

```

#prompt user for yes or no answer

$z='yes'

if [ "$z" = 'yes' ]; then

#these are prompts for user imput
        c=$(command)
        d=$(command)
else

        c=''
        d=''
fi


```

the prompts for user imput inside of the if/then statement "are" functional so i belive my problem lies within the syntax of my if/then statement.

Thanks!

---

### Post by Universal344 on 2009-04-11
Try surrounding yes in $z='yes' with double quotes both at the beginning and in the if statement.  It shouldn't matter but I've had problems with the test command in the past so its worth a try.  If that doesn't work try changing the test command to the test bulletin ([[ ]] instead of [ ]).

---

### Post by Blackdragon1400 on 2009-04-11
thanks, but adding the extra [[ ]] just seemed to stabalize it (if you will) now it seems as if it is skipping the if/then statement completely..it just goes to the commands that i have after the statement.

Any more suggestions? it just wont excecute my commands in the statement

---

### Post by Universal344 on 2009-04-12
Whenever I prompt for user input I use the read command.  This has always worked for me before so you could try writing the user prompts with this command.  The syntax is: read -p (the text in the prompt) $(the name of the var to store the response in).  Hope this helps.

---

