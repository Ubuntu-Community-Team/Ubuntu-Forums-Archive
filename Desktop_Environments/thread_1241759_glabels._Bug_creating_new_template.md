---
title: "glabels. Bug creating new template"
date: 2009-08-16
forum: Desktop Environments
---

### Post by giambolo on 2009-08-16
When creating a new template with custom defined sizes, the second last dialogs asks whether one layout is enough. If I say yes, "one layout is enough", I get the last dialog where I enter the number of rows and the number of columns. No matter what I enter, the template contains one row and one column, thus resulting in one only label per sheet, always.

FIX.
Locate the template in /home/user/.glabels and update manually the values nx and ny as per the following example ...
 
<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.2/">
  <Template brand="MARKIN" part="Cod. 41" size="Other" width="125mm" height="152mm" description="F.to 56x34mm">
    <Label-rectangle id="0" width="56mm" height="34mm" round="3mm" x_waste="0mm" y_waste="0mm">
      <Markup-margin size="2mm"/>
      <Layout nx="2" ny="4" x0="4mm" y0="2mm" dx="59mm" dy="36mm"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>


It should be updated in the soure as well, but I don't know how to suggest this to the developers. Maybe someone can reply to this thread.
Cheers anybody

---

