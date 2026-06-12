---
title: "How do I insert a spreedsheet into a MySQL database?"
date: 2006-01-05
forum: General Help
---

### Post by daller on 2006-01-05
Hi There,

Some of my coworkers are making a calendar-setup in a spreadsheet - Is there an easy way to insert that table (the spreedsheet) in a MySQL table?

I looks something like this:

Date, Place, Contact, Note1, Note2, Note3

Thanks!

---

### Post by aamukahvi on 2006-01-05
You could try the OpenOffice Data Sources thingy. Press F4 to get the appropriate controls showing.

---

### Post by daller on 2006-01-05
And what do I do from there?

- I think of some sort of XML -> MySQL convertion!

```
<?mso-application progid="Excel.Sheet"?>
-
	<Workbook>
-
	<OfficeDocumentSettings>
<DownloadComponents/>
</OfficeDocumentSettings>
-
	<ExcelWorkbook>
<WindowHeight>9000</WindowHeight>
<WindowWidth>13860</WindowWidth>
<WindowTopX>240</WindowTopX>
<WindowTopY>75</WindowTopY>
<ProtectStructure>False</ProtectStructure>
<ProtectWindows>False</ProtectWindows>
</ExcelWorkbook>
-
	<Styles>
<Style ss:ID="Default" ss:Name="Normal"/>
-
	<Style ss:ID="Result" ss:Name="Result" ss:Parent="Default">
<Font ss:Bold="1" ss:Italic="1" ss:Underline="Single"/>
</Style>
-
	<Style ss:ID="Result2" ss:Name="Result2" ss:Parent="Result">
<NumberFormat ss:Format="Currency"/>
</Style>
-
	<Style ss:ID="Heading" ss:Name="Heading" ss:Parent="Default">
<Alignment ss:Horizontal="Center"/>
<Font ss:Bold="1" ss:Italic="1" ss:Size="16"/>
</Style>
-
	<Style ss:ID="Heading1" ss:Name="Heading1" ss:Parent="Heading">
<Alignment ss:Rotate="90"/>
</Style>
<Style ss:ID="co1"/>
<Style ss:ID="co2"/>
<Style ss:ID="co3"/>
<Style ss:ID="ro1"/>
<Style ss:ID="ro2"/>
<Style ss:ID="ta1"/>
-
	<Style ss:ID="ce1" ss:Parent="Default">
<NumberFormat ss:Format="Short Date"/>
</Style>
</Styles>
-
	<Worksheet ss:Name="Ark1">
-
	<Table ss:StyleID="ta1">
<Column ss:Width="40.7905"/>
<Column ss:Width="194.4567"/>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-21T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 21. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-22T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 22. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-23T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 23. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-24T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 24. december &#8211; Merry Christmas!</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-25T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 25. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-26T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 26. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-27T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 27. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-28T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 28. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-29T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 29. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-30T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 30. december</Data>
</Cell>
</Row>
-
	<Row ss:StyleID="ro1" ss:Height="14.7402">
-
	<Cell ss:StyleID="Default">
<Data ss:Type="DateTime">2005-12-31T12:00:00.000</Data>
</Cell>
-
	<Cell ss:StyleID="Default">
<Data ss:Type="String">Today it's the 31. december &#8211; Happy New Year!</Data>
</Cell>
</Row>
</Table>
</Worksheet>
-
	<Worksheet ss:Name="Ark2">
-
	<Table ss:StyleID="ta1">
<Column ss:Width="64.2614"/>
-
	<Row ss:StyleID="ro2" ss:Height="14.5417">
<Cell ss:StyleID="Default"/>
</Row>
</Table>
</Worksheet>
-
	<Worksheet ss:Name="Ark3">
-
	<Table ss:StyleID="ta1">
<Column ss:Width="64.2614"/>
-
	<Row ss:StyleID="ro2" ss:Height="14.5417">
<Cell ss:StyleID="Default"/>
</Row>
</Table>
</Worksheet>
</Workbook>
```

---

### Post by garak on 2006-01-05
export sheet in csv and import it using phpmyadmin

---

### Post by ptmurphy on 2006-01-05
Max is correct, the easiest thing would be to use a CSV file and import using phpmyadmin.  Basically phpmyadmin will take each line of the CSV file and turn it into an SQL statement that looks like this...

INSERT INTO `calendar_table` VALUES ('2005-04-25 20:27:14', 'Room 303', 'John Smith', 'Note 1', 'Note 2','Note 3');

Just in case you ever need to do this manually, or you could create a script that loops through the lines of your spreadsheet and creates the data entry sql statements.

---

### Post by daller on 2006-01-05
Thanks!

I'll use this solution so far...

The problem is, that it's a part of an admin-system on a homepage I'm working on... (Has to be easy for the users!)

What I have so far, is a little php-script that parses a textarea (tabulators means new column)

This is how i find the different cols:

$cols = explode("	", $rows[$i]);

It works, but isn't there another way to explode on tabulators?

And what about newlines?

---

### Post by daller on 2006-01-05
I wonder - When will I start to think?

Explodin' on newline:

$array = explode("\t", $string);

*voila!

Still a hard one on the tabulators exploding!

EDIT: But then again - Maybe I should start reading, instead of learning php out of the thin air!

Explode on tabs:

$array = explode("\t", $string);

---

