---
title: "utf-8 problem"
date: 2009-02-04
forum: General Help
---

### Post by mitjab on 2009-02-04
if i have
header('Content-Type: text/html; charset=utf-8'); 

utf-8 on page works

but if i have

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<title>Sample</title>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />  
<style type="text/css">
	</style>
</head>
<body>

then not working. 

I think that apache does not send header automatically any more. Any idea how to fix that?

---

