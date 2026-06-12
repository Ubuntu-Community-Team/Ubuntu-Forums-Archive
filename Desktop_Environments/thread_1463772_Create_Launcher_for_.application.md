---
title: "Create Launcher for ./application"
date: 2010-04-27
forum: Desktop Environments
---

### Post by scsever on 2010-04-27
I would like to create a launcher for a java application but because it launches with ./application I have been unsuccessful in my attempts.  To launch it now I cd to /opt/tools/test/ and then launch it with ./application.  The problem is that I have no idea how to make this happen in one command.  

Thanks,

---

### Post by dv3500ea on 2010-04-27
```
/opt/tools/test/application
```

---

### Post by scsever on 2010-04-27
I've already tried this.
I'm not familiar with why some applications need ./ to launch them but this is one.  That's why I have to cd to /opt/tools/test/ and then launch with ./application.
If I try /opt/tools/test/application it won't run.
Maybe there is something I need to do to the file so ./ isn't needed?  But I have no idea.

Thanks,

---

### Post by dv3500ea on 2010-04-28
That's strange, '/opt/tools/test/application' is the same as './application' when in '/opt/tools/test/'. My only guess is that there are other files in that directory that application depends on.

Try making a file in '/opt/tools/test/' called 'run-application'
with the contents:
```

#!/bin/sh
cd /opt/tools/test/
./application

```
then run 
```
chmod +x /opt/tools/test/run-application
```

Then create a launcher with path '/opt/tools/test/run-application'

---

### Post by scsever on 2010-04-30
I found someone in our local LUG that knew what to do, the solution was to use this shortcut:  bash -c "cd /opt/tools/test ; ./application"

Thanks,

---

