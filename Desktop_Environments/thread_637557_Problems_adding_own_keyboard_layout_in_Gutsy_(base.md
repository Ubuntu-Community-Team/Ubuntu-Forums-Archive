---
title: "Problems adding own keyboard layout in Gutsy (base.xml)"
date: 2007-12-11
forum: Desktop Environments
---

### Post by rrohde on 2007-12-11
Hi everyone!  :)

I got an interesting issue here: We require in our environment a custom made keyboard layout which needs to be added to /etc/X11/xkb/rules/base.xml. 

Under Feisty, this worked like a charm. Under Gutsy, however, this doesn't work anymore. The syntax of the configuration files under /etx/X11/xkb/rules seems to have changed enough to stop this from working.

I am baffled at the syntax and can't seem to make this work anymore, even though I tried to adapt the syntax to the new  one - to no avail.

Here is the original layout that I would like to inject into base.xml This worked exactly like this under Feisty - however this breaks the option to select a KB under X in Gutsy completely.

Note: The actual keyboard definitions live already under /etc/X11/xkb/symbols.

```
<layoutList>

    <layout>
      <configItem>
        <name>eu3-qwerty</name>
        <shortDescription>EU3 qwerty</shortDescription>
        <description>EU3 qwerty keyboard layout</description>
      </configItem>
      <variantList>
          <variant>
            <configItem>
              <name>green</name>
              <description>Green</description>
            </configItem>
          </variant>
          <variant>
            <configItem>
              <name>red</name>
              <description>Red</description>
            </configItem>
          </variant>
          <variant>
            <configItem>
              <name>yellow</name>
              <description>Yellow</description>
            </configItem>
          </variant>
      </variantList>
    </layout>
```



My questions: 
- How can I adapt this code to work under Gutsy? 
- What other files besides base.xml does the layout need to be referenced? 


Cheers, 
Rainer

---

