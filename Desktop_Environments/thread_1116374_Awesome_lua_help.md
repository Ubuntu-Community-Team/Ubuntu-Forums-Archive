---
title: "Awesome lua help"
date: 2009-04-04
forum: Desktop Environments
---

### Post by PurposeOfReason on 2009-04-04
I'm trying to get awesome to display the avg. temp of my two cores. For the code, I have this
```

function cpu(cpwidget)
    local temperature = 0
    local temp1 = 0
    local temp2 = 0 
    local sensors = io.popen('sensors')
    temp1 = '/usr/bin/sensors | grep Core\ 0| paste -s | cut -c15-16'
    temp2 = '/usr/bin/sensors | grep Core\ 1| paste -s | cut -c15-16'
    temperature = temp1 + temp2
        sensors:close()
 
    temperature = temperature / 2
 
    cpwidget.text = spacer..temperature..'C' 
end

```I know that what I need to do is somehow get the sensors output into a format that can be read so that I could then make another variale 'x' and put local x = temp1:read()

I'm just not sure how to do this in lua.

---

