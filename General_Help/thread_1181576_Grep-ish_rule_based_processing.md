---
title: "Grep-ish rule based processing?"
date: 2009-06-08
forum: General Help
---

### Post by redxine on 2009-06-08
I'm trying to make a one-line script that will announce the current weather conditions. So far I have:
```
weather PHX | grep -A 3 "Weather Conditions at" | tail -n 1 | padsp espeak
``` 


The problem is that the output is in the form of a table like this:
```
Weather Conditions at 10:51 PM MST on 07 Jun 2009 for Phoenix, AZ.
Temp(F)    Humidity(%)    Wind(mph)    Pressure(in)    Weather
========================================================================
  83          18%         SW at 4       29.73      Mostly Cloudy
```

And espeak (I) wants them to be read as:```


Weather Conditions at 10:51 PM MST on 07 Jun 2009 for Phoenix, AZ:
Skies are Mostly Cloudy. The Current temperature is 83 degrees. The 
Humidity is 18 per-cent. The Wind is South-West at 4 miles-per-hour, and 
the pressure is 29.73 inches.
```

Is there any kind of rule based program or script that can format the data like this?

---

### Post by bluefrog on 2009-06-08
your output is rather strange as it differs from what I get and what I get is plainly readable and understandable with espeak.

---

### Post by bluefrog on 2009-06-08
.

---

### Post by redxine on 2009-06-08
Oops.... forgot to mention i'm on fedora... :lolflag:
They must use a different weather script. I should just be able to copy it from ubuntu then right?

Also, I'd rather not have all the abbreviations. Wind is from the E at 6 MPH.

---

### Post by kpkeerthi on 2009-06-08
1. Save the attached pre-process.sh to your HOME folder and grant execute permission.

2. Assuming you have a command that generates the below text highlighted,
```

[COLOR="Green"]Weather Conditions at 10:51 PM MST on 07 Jun 2009 for Phoenix, AZ.
Temp(F)    Humidity(%)    Wind(mph)    Pressure(in)    Weather
========================================================================
  83          18%         SW at 4       29.73      Mostly Cloudy[/COLOR]

```
you need to pipe the output to pre-process.sh, like so:

```
 [COLOR="Red"]cat weather.data[/COLOR] | ./pre-process.sh
```
(In my case weather.data is the file that contains the content highlighted in green)

**Here is the output:**
```

Weather Conditions at 10:51 PM MST on 07 Jun 2009 for Phoenix, AZ:
Skies are Mostly Cloudy. The Current temperature is 83 degrees. The
Humidity is 18 per-cent. The wind is South West at 4 miles-per-hour, and
the pressure is 29.73 inches

```
* Replace the command highlighted in red with the one that generates the output text in green.

---

