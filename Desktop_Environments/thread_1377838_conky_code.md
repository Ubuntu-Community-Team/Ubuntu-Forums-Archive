---
title: "conky code"
date: 2010-01-10
forum: Desktop Environments
---

### Post by 3948ctyj on 2010-01-10
look at this conky code

${color white}${font OpenLogos:size=14}Ubuntu Linux ${font}${font
Vera:size=9}$alignr ${time %a } ${time %e %B %G} | ${time %I:%M
%P}${font}
${color #5da5d3}User ${hr 1}

see that straight line after %B%G          that puts that symbol in that space   just before the time with hr,min.
and pm/am.   
If I get rid of that and move the ${time %I:%M%P} down 1 line it will display down 1 line ???
and what is the ${font}  after it for..????

---

### Post by m_duck on 2010-01-11
To get rid of the line, just delete it and to move the time down to the next time, just move the ${time %I:%M %P} on to a new line. You may want to precede that with ${alignr} to right-align it as on the line above.

The ${font} resets the font properties to whatever the defaults in your conky config are (in the top section before TEXT). For example, in the code you posted, the font will be default to begin with, then change to openlogos in size 14 before printing anything, then (unneccessarily) go back to defaul before instantly changing to Vera size 9, then back to default after the time. Set the default to whatever you want the majority of the text to be because ${font} is quicker to type than ${font SomeFontName:size=x} each time.

HTH

---

