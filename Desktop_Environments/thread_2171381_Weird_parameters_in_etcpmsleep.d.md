---
title: "Weird parameters in /etc/pm/sleep.d"
date: 2013-08-30
forum: Desktop Environments
---

### Post by TheOnlyChosenOne on 2013-08-30
Hi

I have a script that has to be executed after resume from suspend. I have this right now:
```
#!/bin/bash 
case "$1" in
    resume)
        sudo -u user env DISPLAY=:0 sudo /home/user/script.sh
        ;;
esac
```
This works, but it turns my screen black because of 'DISPLAY=:0'. If I remove this parameter, it doesn't work anymore.
Does anyone know why?

Thanks.

Edit: The fact that it works or not doesn't have to do with the 'DISPLAY=:0' parameter.

---

