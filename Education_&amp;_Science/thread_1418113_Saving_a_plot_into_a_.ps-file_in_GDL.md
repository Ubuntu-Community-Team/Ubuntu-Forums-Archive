---
title: "Saving a plot into a .ps-file in GDL"
date: 2010-02-28
forum: Education &amp; Science
---

### Post by Kettarie on 2010-02-28
Hi, all!
I have some problems with saving a  plot in GDL into a .ps -file. 

I'm trying to do it that way:

pro contour_plot
   set_plot, 'ps' 
   device, filename='test.ps'
   ; device, 'test.ps'   

   contour, data, nlevels=10, /fill 
   title = 'contour plot, level number = 10'
   device, close
   set_plot, 'X'

end

(data is a double array)
I get an error % DEVICE: Incorrect number of arguments.

When I'm trying

pro contour_plot
   set_plot, 'ps
   device, filename='test.ps'
   ; device, 'test.ps'   

   contour, data, nlevels=10, /fill 
   title = 'contour plot, level number = 10'
   device, close
   set_plot, 'X

end

the error is % SET_PLOT: Device not supported/unknown: PS ; TO SAVE THE RESULT INTO A .PS-FILE


Maybe someone knows, how to fix it? Do I need some additional libraries to be added to GDL to make it work?
Can I save my plot into a .jpg-file?

---

