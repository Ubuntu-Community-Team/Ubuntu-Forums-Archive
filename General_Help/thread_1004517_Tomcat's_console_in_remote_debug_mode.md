---
title: "Tomcat's console in remote debug mode"
date: 2008-12-07
forum: General Help
---

### Post by McBianconi on 2008-12-07
I'm trying to get my tomcat's (tomcat 5.5) console output in Ubuntu, but got nothing untill now

What I'm doing is basically calling this script to remotely debug an app:
```
#!/bin/sh
export JPDA_ADDRESS=9797
export JPDA_TRANSPORT=dt_socket

PRGDIR=`dirname "$0"`
EXECUTABLE=catalina.sh

exec "$PRGDIR"/"$EXECUTABLE" jpda start
```

In Windows it works well, but in Ubuntu, it starts ok and everything, but I don't get the console output :x

If I call "jpda run", I can see the console output, But It starts right after as I run the script, It doesn't wait for me to connect

I don't know if my problem is well explained, if you need more info, just ask

Thanks in advance.

---

### Post by jamesstansell on 2008-12-07
> **McBianconi said:**
> I'm trying to get my tomcat's (tomcat 5.5) console output in Ubuntu, but got nothing untill now


exec "$PRGDIR"/"$EXECUTABLE" jpda start[/CODE]

In Windows it works well, but in Ubuntu, it starts ok and everything, but I don't get the console output :x

If I call "jpda run", I can see the console output, But It starts right after as I run the script, It doesn't wait for me to connect


I'm not familiar with tomcat, but I wonder if the start command is storing the output to a file?

You might be able to tell by reading throught the shell script.  Or if not then the fuser or lsof commands could be of interest.  (They are good to know how to use in any case.)

---

### Post by McBianconi on 2008-12-08
Thanks for the help!

I Just looked at the catalina.sh script and saw that it was saving the logs in a folder :O

The code was like: 
      [...] org.apache.catalina.startup.Bootstrap "$@" start \
      >> "$CATALINA_BASE"/logs/catalina.out 2>&1 & [...]

And I changed to:
      [...] org.apache.catalina.startup.Bootstrap "$@" start [...]


But now its acting just like the "run", its automatically starting after I call it, not waiting for me to connect

Any ideas?

---

