---
title: "Works in 8.10 but not 8.04 - why?"
date: 2009-03-08
forum: General Help
---

### Post by KayakJim on 2009-03-08
I have the following code (that I found in and shamelessly copied from one of the several "Post your .bashrc" threads) in my .bashrc on my local system (Ubuntu 8.10) and my server (Ubuntu 8.04). It works great on my 8.10 system but not on my 8.04 system.

Any ideas why this is the case and how to get it to work properly on both systems would be much appreciated.

```


function pre_prompt {
  newPWD="${PWD}"
  user="whoami"
  host=$(echo -n $HOSTNAME | sed -e "s/[\.].*//")
  datenow=$(date "+%a, %d %b %y")
  let promptsize=$(echo -n "--($user@$host ddd, DD mmm YY)---(${PWD})---" | wc -c | tr -d " ")
  let fillsize=${COLUMNS}-${promptsize}
  fill=""
  while [ "$fillsize" -gt "0" ]
  do
    fill="${fill}—"
    let fillsize=${fillsize}-1
  done
  if [ "$fillsize" -lt "0" ]
  then
      let cutt=3-${fillsize}
      newPWD="...$(echo -n $PWD | sed -e "s/\(^.\{$cutt\}\)\(.*\)/\2/")"
  fi
}
PROMPT_COMMAND=pre_prompt

export black="\[\033[0;38;5;0m\]"
export red="\[\033[0;38;5;1m\]"
export green="\[\033[0;38;5;2m\]"
export yellow="\[\033[0;38;5;3m\]"
export blue="\[\033[0;38;5;4m\]"
export magenta="\[\033[0;38;5;55m\]"
export cyan="\[\033[0;38;5;6m\]"
export white="\[\033[0;38;5;7m\]"
export coldblue="\[\033[0;38;5;33m\]"
export smoothblue="\[\033[0;38;5;111m\]"
export iceblue="\[\033[0;38;5;45m\]"
export turqoise="\[\033[0;38;5;50m\]"
export smoothgreen="\[\033[0;38;5;42m\]"

PS1="$green&#9484;&#9472;($coldblue\u@\h \$(date \"+%a, %d %b %y\")$green)&#9472;\${fill}&#9472;($coldblue\$newPWD\
$green)&#9472;&#9472;&#9472;&#9472;&#9488;\n$green&#9492;&#9472;($coldblue\$(date \"+%H:%M\") \$$green)&#9472;>$white "

```

Here are the screenshots to see the difference but basically the 8.04 prompt wraps to the next line instead of fitting on one line.

8.10 prompt
[IMG]http://www.bluefiredev.com/images/prompt_8_10.png[/IMG]


8.04 prompt
[IMG]http://www.bluefiredev.com/images/prompt_8_04.png[/IMG]

---

### Post by Slim Odds on 2009-03-08
Maybe because you're comparing apple with oranges?

They are not in the same directory, therefore not producing the same results.

Maybe some bad math?

P.S. What versions of bash are these using?

---

### Post by KayakJim on 2009-03-08
The lines:

```

  let promptsize=$(echo -n "--($user@$host ddd, DD mmm YY)---(${PWD})---" | wc -c | tr -d " ")
  let fillsize=${COLUMNS}-${promptsize}

```

determines the size of the prompt (including the path) and subtracts it from the width of the window.

The results are the same regardless of what directory path I am in - the 8.10 prompt is always the correct width while the 8.04 prompt always overwraps.

My 8.10 system is using GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu).

My 8.04 system is using GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)

---

### Post by KayakJim on 2009-03-10
Any other ideas from anyone would be appreciated.

---

### Post by KayakJim on 2009-03-20
One last bump

---

