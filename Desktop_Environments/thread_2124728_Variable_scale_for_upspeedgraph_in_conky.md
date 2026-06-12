---
title: "Variable scale for upspeedgraph in conky"
date: 2013-03-11
forum: Desktop Environments
---

### Post by mattblhs on 2013-03-11
First idk if this is the write forum seeing how this is my first post here ever.
With that said I was wonder if it is possible to have a variable scale for the upspeedgraph and downspeedgraph objects in Conky.

Thanks

---

### Post by Frogs Hair on 2013-03-11
Hello and Welcome 

The location of post is fine . Conky can display upload and download speed in different ways of that is what you mean. Something more specific would be helpful. An indicator bar placed over a graph image is possible. There is one example of an indicator in the screen shot.

---

### Post by mattblhs on 2013-03-12
No when I say variable scale i mean if the current max in the graph is say 100 kB/s then the scale is 100 kB/s but if the max suddenly goes to 200kB/s then the scale on the graph changes to 200kB/s automatically. I hope that clears it up a little.

---

### Post by Frogs Hair on 2013-03-12
You could use a fixed  image of grid lines and show activity over them, but have not seen an expandable graph .
 
```
sudo apt-get install conky-all
``` 

```
man conky
```

---

