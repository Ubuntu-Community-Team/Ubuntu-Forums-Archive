---
title: "conkyrc if statement help"
date: 2009-04-21
forum: Desktop Environments
---

### Post by I[AM]SMRT on 2009-04-21
I'm trying to get play data from banshee, and found that "exec banshee-1 --query-artist" works but I'm having problems with the if statements. I don't want it to display anything if banshee isn't running (just error statements) but if it is, I want it to display the info when banshee IS running, so I wrote the following:

```
${voffset -10}NOW PLAYING ${hr 2}
${if_running banshee-1}
${font Webdings:size=14}x${font} ${execi 1 banshee-1 --query-artist}
${font Webdings:size=14}x${font} ${execi 1 banshee-1 --query-title}
${font webdings:size=14}x${font} ${execi 1 banshee-1 --query-album}
${endif}
```

At the top of the .conkyrc file I have:

```
# Update interval in seconds
update_interval 1
```

With this code it doesn't display anything...ever, even when I run banshee :(.

Also, for my other if statements, if they're not true (so conky doesn't display anything there) there's still kind of a big space in its place. How can I get rid of this?

---

