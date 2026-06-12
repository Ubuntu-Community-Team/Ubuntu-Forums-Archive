---
title: "Conky config problem"
date: 2010-12-06
forum: Desktop Environments
---

### Post by alanwalterthomas on 2010-12-06
I've been working on a cool conky config for a while, but have a small problem I don't know how to fix.

I have an ATI video card & am using aticonfig --odgc to get the core & memory clocks, the gpu load & temp. The problem is this:

I use this to get the value of one of the variables, in this case GPU Load, & feed it to a script that changes the colour (blue, yellow, red) depending on the GPU utilization:

#####################
GPU Load $alignr ${execpi 6 aticonfig --odgc | grep load | cut -c32-33 | xargs ~/Documents/Computer/Conky/GPULOADcolorize.sh}%$color
####################

If the GPU load is double digit, it works because cut -c32-33 gives me ##. However, if the GPU load is single digit, like 3% or 0%, the second digit is a % sign, which doesn't fit into the colorize script, & I get something like 0%% at the medium speed colour.

The colorize script is:
###################
#!/bin/bash
# colorize.sh

# Note: Assign color7, color8, and color9 to SLOW, MEDIUM, and FAST respectively
#   your .conkyrc
 
SLOW=33
MEDIUM=67
 
if [[ $1 -lt $SLOW ]]
   then echo "\${color7}"$1    # SLOW
elif [[ $1 -gt $MEDIUM ]]
   then echo "\${color9}"$1    # FAST
else echo "\${color8}"$1       # MEDIUM
fi
 
exit 0
######################

How can I get this to work with single & triple digit values, & exclude the % sign?


Sample aticonfig --odgc below

Default Adapter - ATI Radeon HD 4600 Series
                            Core (MHz)    Memory (MHz)
           Current Clocks :    165           250
             Current Peak :    750           1000
  Configurable Peak Range : [300-800]     [1000-1050]
                 GPU load :    0%


P.S.
I bet the best solution would be to change the colorize script so that it can take 0%, 50%, 100% etc. & take off the "%" or only consider #'s, & then pass the value through the rest of the script, & change the conkyrc to cut 4 characters.
I've no idea how to do that. I think that can be done in the script, but would someone be kind enough as to show me how?

---

### Post by stinkeye on 2010-12-06
Instead of using  **cut -c32-33** to get your load
what about using 
```
  awk '{print $4}' | tr -d %
```
Works with the Sample aticonfig --odgc you posted.
[COLOR="DarkRed"]GPU[/COLOR] [COLOR="Blue"]load[/COLOR] [COLOR="SeaGreen"]:[/COLOR] [COLOR="DarkOrange"]0%[/COLOR]
[COLOR="#8b0000"]$1[/COLOR]..[COLOR="#0000ff"]$2[/COLOR]..[COLOR="#2e8b57"]$3[/COLOR].[COLOR="#ff8c00"]$4[/COLOR]


So your line in your conky would be...
```
GPU Load $alignr ${execpi 6 aticonfig --odgc | grep load | [COLOR="Magenta"]awk '{print $4}' | tr -d %[/COLOR] | xargs ~/Documents/Computer/Conky/GPULOADcolorize.sh}%$color
```

---

### Post by alanwalterthomas on 2010-12-07
THANK YOU!

That worked perfectly. That trick will be useful for other stuff too.

---

