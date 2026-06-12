---
title: "Using Conky execpi variable with Bash conditional statement"
date: 2017-03-31
forum: Desktop Environments
---

### Post by namruf152 on 2017-03-31
I'm trying to write a simple "pinger" script which will periodically  try to reach given IP address and output a colored message with  information if it is available or not.

  I face the problem in which I can't set custom color inside Bash conditional statement. The Bash code has been inserted into *execpi* variable. Every time when I try to run *Conky* I get Bash error *sh: 1: Bad substitution*.

  Conky TEXT section:
```

${color grey}Module_1: ${color}: ${execpi 10 if ping -c 1 -W 2 192.168.1.1 > /dev/null; then echo ${color green}"Success"${color}; else echo ${color red}"Failed"${color}; fi} | ${color grey}Module_2: ${color} ${execpi 10 if ping -c 1 -W 2 192.168.1.2 > /dev/null; then echo ${color green}"Success"${color}; else echo ${color red}"Failed"${color}; fi}
```

Should the *color *variable be placed in some different way?

---

### Post by Frogs Hair on 2017-03-31
Have you tried an html color value rather than the word ? I have many different conky themes and multiple colors can be handled different ways.   

One way I've done it follows.

```

# Color scheme #

default_color FF0033
color1 6495ED
color2 ffffff
color3 ff0066

```

In the cpu line further into the syntax with 2 colors.
```
${color1}CPU1: ${cpu cpu1}% $alignr${color3}${cpubar cpu1 8,60}
```

---

### Post by again? on 2017-03-31
Put the conditonal statement in a bash script and escape the "$"s with "**\**".
(make executable)

```
#!/bin/sh

#Module1
if ping -c 1 -W 2 192.168.1.1 > /dev/null; then 
    echo "\${color grey}Module_1: \${color green}Success\${color}"
else 
    echo "\${color grey}Module_1: \${color red}Failed\${color}"
fi

#Module2
if ping -c 1 -W 2 192.168.1.2 > /dev/null; then 
    echo "\${color grey}Module_2: \${color green}Success\${color}"
else 
    echo "\${color grey}Module_2: \${color red}Failed\${color}"
fi

```
Then call the script in conky using [COLOR=#ff0000]your path[/COLOR] to script.
```
${execpi 10 [COLOR=#ff0000]/path/to/script[/COLOR]}
```

---

### Post by namruf152 on 2017-04-03
Thank you for proposed solution. The problem was with not escaped dollar signs. After I've added the backslashes everything works properly. Topic can be closed.

---

