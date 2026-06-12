---
title: "[SOLVED] Anybody know VB6?"
date: 2008-12-19
forum: General Help
---

### Post by CrusaderAD on 2008-12-19
I know this is a visual basic question, but I hate the VB forums. Ubuntu Forum Members always helps me out. I have a loop printing a record set like so:

```

   If Not (RS.EOF) Then
           
           While Not RS.EOF
                        'MsgBox "first record"
                        'printer.CurrentX = 5
                        'printer.Copies = 1
                        Printer.ScaleMode = 1 ' vbTwips
                        'MsgBox "after scale"
                        Printer.Height = 1 * 1440
                        Printer.Width = 2 * 1400
                        'MsgBox "after h and w"
                        Printer.CurrentY = 150
                        Printer.FontName = "arial"
                        Printer.FontSize = 12
                        'MsgBox "after font"
                        
                        Printer.Print Tab(3); RS("productID") & " " & RS("name")
                        'MsgBox "after all before spool"
                        Printer.EndDoc
                        'MsgBox "after spool"
                        
                        
        RS.MoveNext
        Wend
        RS.Close
```

The result is that it prints 30 pages because there are about 30 records. How do I get them on one page?

---

### Post by Titan8990 on 2008-12-19
You may have better luck if you report your post and ask that it is moved to the programming talk forums. Those forums are very active and I have always been able to get assistance there.

---

### Post by CrusaderAD on 2008-12-19
I'll try that... I was hoping to get some kind of resolution sooner. We'll see. Thanks!

---

### Post by CrusaderAD on 2008-12-31
The Printer.Enddoc needed to be outside the loop like so:
```

   If Not (RS.EOF) Then
           
           While Not RS.EOF
                        'MsgBox "first record"
                        'printer.CurrentX = 5
                        'printer.Copies = 1
                        Printer.ScaleMode = 1 ' vbTwips
                        'MsgBox "after scale"
                        Printer.Height = 1 * 1440
                        Printer.Width = 2 * 1400
                        'MsgBox "after h and w"
                        Printer.CurrentY = 150
                        Printer.FontName = "arial"
                        Printer.FontSize = 12
                        'MsgBox "after font"
                        
                        Printer.Print Tab(3); RS("productID") & " " & RS("name")
                        'MsgBox "after all before spool"
                        
                        'MsgBox "after spool"
                        
                        
        RS.MoveNext
        Wend
        RS.Close
        Printer.EndDoc

```

---

