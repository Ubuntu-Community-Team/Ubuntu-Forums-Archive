---
title: "Shell script to monitor several parallel commands"
date: 2009-06-02
forum: General Help
---

### Post by tarekeldeeb on 2009-06-02
Hello all,

I'm still a linux newbie, I want to run a script that does the following psuedo code:

```
operation1&;
pid1=$!;
operation2&;
pid2=$!;

running = true;
while (running) {
 if($pid1 is running || $pid2 is running) then
   running = true;
 else
   running = false;
 fi
}

build_report; # based on operation1 and operation2
```

I want to run the operations in parallel to gain better performance, but the report builder has to wait till they finish

Can anyone help me with this ?

Thanks in advance,

Tarek

---

### Post by unutbu on 2009-06-02
[PHP]#!/bin/sh
# I learned this here: http://www.linuxquestions.org/questions/programming-9/bash-script-monitoring-running-pid-222731/

test1.sh &
pid1=$!
test2.sh &
pid2=$!

if wait "$pid1" && wait "$pid2"
then
  echo program terminated
else
  echo program terminated abnormally
fi
[/PHP]

---

### Post by tarekeldeeb on 2009-06-02
> **unutbu said:**
> [PHP]#!/bin/sh
# I learned this here: http://www.linuxquestions.org/questions/programming-9/bash-script-monitoring-running-pid-222731/

test1.sh &
pid1=$!
test2.sh &
pid2=$!

if wait "$pid1" && wait "$pid2"
then
  echo program terminated
else
  echo program terminated abnormally
fi
[/PHP]


Works perfectly! Thanks.

I have been trying, maybe I reached an easier way. But still has an understood problem to me:

```
#!/bin/bash
./p1.sh &
./p2.sh &

while [ `jobs -l | wc -l` -gt 0 ]
do
        echo Sleeeeep ..
        #jobs -l
        sleep 1s
done

echo finished!

```

This permits the printing of some log messages. You know what? When the "jobs -l" in the loop is uncommented, everything works as expected. When it is commented it never gets out of the loop !!

I cannot understand this manor.

Anyway .. thanks for your script .. it does the job perfectly.

Tarek

---

### Post by Ole Tange on 2010-06-14
GNU Parallel [http://www.gnu.org/software/parallel/](http://www.gnu.org/software/parallel/) is a general solution to running jobs in parallel in the shell.

(echo operation1; echo operation2) | paralllel

Watch the intro video: [http://www.youtube.com/watch?v=LlXDtd_pRaY](http://www.youtube.com/watch?v=LlXDtd_pRaY)

---

