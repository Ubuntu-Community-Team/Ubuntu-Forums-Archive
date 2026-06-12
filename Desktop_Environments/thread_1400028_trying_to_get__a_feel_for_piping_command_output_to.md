---
title: "trying to get  a feel for piping command output to grep"
date: 2010-02-06
forum: Desktop Environments
---

### Post by bluethundr on 2010-02-06
Hi there,

 I am reviewing some of the basics and trying to get a "feel" for how output is chained from command to command. 


 I am trying to build a solution with awk

To begin let's say that I want to grep the output of top to see if firefox is running...

```

$ top | grep firefox

```

Simple.

What if I want to switch gears for a bit and search the output of top and refine what I'm seeing with a bit of formatting:


```

$ top | awk '{ print "User: " $3 " PID: " $2 " Command: " $13}'

```

And as a final step let's say I wanted to grep for a specific command:

```

$ top | awk '{ print "User: " $3 " PID: " $2 " Command: " $13}' | grep firefox

```


That last command doesn't work. I would like to turn this process into few handy environment variables and replace myself with a small shell script. ;)

I selected "other OS" here, because this question is about as generic as it comes and applies to all unix like systems I can think of.

---

### Post by jken146 on 2010-02-06
This is because top has an interactive interface (you have to press q to exit, for example). It doesn't just output everything to stdout and terminate, so it's waiting for input even though you're piping the output to different programs.  Run your last command, then press q and you'll see what you were aiming for.

Have a look at ps.

---

