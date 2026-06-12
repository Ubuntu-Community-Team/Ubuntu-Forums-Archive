---
title: "conky- cpu temp"
date: 2009-06-10
forum: Desktop Environments
---

### Post by blur xc on 2009-06-10
Does the acpitemp variable return the cpu temp on an intel core 2 duo processor?  And what about the acpifan?

thanks,
BM

---

### Post by blur xc on 2009-06-11
Well, I've been doing a lot of reading on the subject, and information varies greatly from source to source...  I followed these instructions [http://www.lm-sensors.org/wiki/iwizard/Detection](http://www.lm-sensors.org/wiki/iwizard/Detection) and this is what I get from running the sensors command:
```

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +2.00 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.24 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.02 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.10 V
fan1:       1767 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +35.0°C  (high = +78.0°C, crit = +100.0°C) 
```

I'm a little confused w/ the ouput from temp3.  The instructions to fix it on this page are a bit confusing- [http://www.lm-sensors.org/wiki/iwizard/WrongTemps](http://www.lm-sensors.org/wiki/iwizard/WrongTemps)

I assume Core 0 and Core 1 are the two cores of my processor.  fan1 is my cpu fan, since that's the only fan I have that plugs into my mobo (case fans are simple molex jobs)...  So, how do I get the core temps and fan speed into my conky?

BTW- I've been up and down this thread 100 times- [http://ubuntuforums.org/showthread.php?t=657086](http://ubuntuforums.org/showthread.php?t=657086)

Thanks,
BM

---

### Post by Greenwidth on 2009-06-11
For CPU temp add this to conky script:
```
${execi 30 sensors | grep "Core 0" | cut -d "+" -f2 | cut -c1-6}
```
Add twice and change second to "Core 1" to show both. 

Not sure how to add fan speed but see link (and links on page) for a lot of conky help:
[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

---

### Post by m_duck on 2009-06-11
For the fan speed, you could use something like:```
${execi 30 sensors | grep "fan1:" | awk '{ print $2 " " $3 }'
```

---

### Post by blur xc on 2009-06-11
Awesome, I'll try both those lines when I get home...  But rather than just throwing me a bone- how bout teaching me bit so I might have a fighting chance at figuring out a bit on my own next time.

Could you explain the logic behind those two lines of code?  I snagged the one from that old thread to get the nvidia gpu temp, but I can't understand any of it.

BM

---

### Post by m_duck on 2009-06-11
Sure. My descriptions may not be technically accurate but are what I have taught myself/google has taught me...

For both of the commands, the **${execi 30** part is conky specific which basically says, "Execute the following command every 30 seconds and display the output". There are a numbe of variants, which are listed (along with all the other conky commands) [here]("http://conky.sourceforge.net/variables.html"). The command after this part, you could execute in a terminal (minus the ending curly brace) and get the same output as conky would give you.

**sensors** is obviously the command which gives the ouput you gave in the first post.

The pipe, **|**, means the output of the command to the left is fed into the command on the right (AFAIK).

**grep "Core 0"** will display any lines which contain the string "Core 0" but ignore all others. In this case each of the greps will display only one result. There is an option for grep to display only one result, amongst other things. For that check the grep man page, **man grep**.

The **cut** command does what it says on the tin, cuts letters. The **-d** part sets the delimiter for the current cut, and in this case is "**+**". Basically, this cuts the given string into certain "fields", each separated by a **+** symbol. The **-f** option is to choose the field required, in this case field 2.

The second cut command is similar but uses the **-c** option. This means cut all the characters from 1 to 6 (inclusive) in this case.

In my post, the grep command is used in the same way as above, and the awk command is used similarly to the first cut in Greenwidth's post. It takes the input from **sensors | grep "fan1:"** and is told to print the 2nd and 3rd fields, separated by a space. I think awk defaults to having whitespace as its delimiter but I'm not sure as I've only started trying to use it recently myself.

The way I leant these things was to look at what other people were using/posting and then break them down and see which each piece was doing. Also google and man pages are your friends :D

HTH

EDIT: Wow, got a bit involved there...

---

### Post by blur xc on 2009-06-12
Wow- Thanks!  I'm starting to understand the logic, but the syntax is still tough.  IMO, the explanations in the man [command] are lacking some information.  The show you what the operators are but the leave out example of how the syntax of the command should be written.  At least it's a bit vague...  I imagine in time I'll start to pick up on it...

Thanks again! 
BM

---

