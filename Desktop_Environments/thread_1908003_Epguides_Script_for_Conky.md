---
title: "Epguides Script for Conky"
date: 2012-01-12
forum: Desktop Environments
---

### Post by tachibana on 2012-01-12
Hi Everyone!
I developed a simple script for conky to get next episode date from epguides.com

Just put the script file somewhere then configure your conky to execute the script given intervals. I actually prefer to execute script twice a day.

This is the example code for your .conkyrc
```
${font}${color6}${texeci 43200 ~/scripts/epguides/epguides.sh "How I Met Your Mother" "Big Bang Theory" "Chuck"}
```

Double quoted show names are the arguments for the script. Before put your favorite show there i suggest that check the show's name from [http://epguides.com]("http://epguides.com")

Have fun!

---

