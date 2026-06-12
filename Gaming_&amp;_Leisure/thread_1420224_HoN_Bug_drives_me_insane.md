---
title: "HoN Bug drives me insane"
date: 2010-03-02
forum: Gaming &amp; Leisure
---

### Post by Badirca Dorian on 2010-03-02
HI , i downloaded HoN Client a week ago and since then trying to have some games. But every time i enjoy a game ... boom ... the game stops ( sometimes i can move the mouse ) and comes back in 30sec - 1 min, and sometimes dosen't come back at all. I ran the game via terminal : 

Entity: line 47: parser error : Comment not terminated 
<!--<beam
                delay="100"
            
                bone_a="_bone_fx_{a}
        <!--    
          ^
Entity: line 62: parser error : Opening and ending tag mismatch: template line 6 and particlesystem
        </particlesystem>
                         ^
Entity: line 63: parser error : Opening and ending tag mismatch: particlesystem line 5 and definitions
    </definitions>
                  ^
Entity: line 71: parser error : Opening and ending tag mismatch: definitions line 3 and effect
</effect>
         ^
Entity: line 75: parser error : Premature end of data in tag effect line 2

No ideea what that means :)) Can you guys please help me ? 
Thanks!

---

### Post by IceDoE on 2010-03-03
Have you tried posting this on the HoN forum under the linux support section?

---

### Post by Badirca Dorian on 2010-03-03
Yes , i tried , but no response there .

---

### Post by Ferrat on 2010-03-03
Oh they've done it again ^^the guys at S2 are great at code but for some reason they tend to forget to dubble check the XML 

[COLOR="Red"]Entity: line 47: parser error : Comment not terminated [/COLOR]

That's your problem or at least a big part of it, someone of the guys has made a change to the XML and forgotten to "close" the comment

```
<!--<beam
delay="100"

bone_a="_bone_fx_{a}
<!--
```

should probably be 

```
<!--<beam
delay="100"

bone_a="_bone_fx_{a}
-->
```

if you look in you HoN folder you should find a few XMLs see if you can find the one where the lines 47+ says the same as 

[COLOR="Red"]<!--<beam
delay="100"

bone_a="_bone_fx_{a}
<!-- [/COLOR]


and just change the last one from [COLOR="Red"]<!--[/COLOR] to [COLOR="SeaGreen"]-->[/COLOR]

That should help :) the following erros are probably due to that first one

---

