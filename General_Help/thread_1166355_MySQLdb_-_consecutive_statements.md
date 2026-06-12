---
title: "MySQLdb - consecutive statements"
date: 2009-05-21
forum: General Help
---

### Post by clintmiskell on 2009-05-21
Hey guys, wondering if anyone has a better way to do this. Seems to work,  but it seems like it could be easier (no list hopefully). I have a bunch of huge  queries that I keep in an external module. I assign each statement to a  variable, then add the variable to a  list: 
 
statements.py 
var1="""some insert  statement""" 
var2="""some insert statement""" 
var3="""call some  proceedure""" and so-on. 
 
list = [var1, var2,  var3] 
____________________________________________________________ 
execute.py: 
 
import  MySQLdb, settings, mailer, statements 
 
def  sql(statement): 
try: 
con = MySQLdb.connect  (host=settings.server,user=settings.user,passwd=settings.password,db=settings.database) 
cursor  =  con.cursor() 
cursor.execute(statement) 
cursor.close() 
con.close 
 
except  MySQLdb.Error, e: 
error = "Warehouse Error %d: %s" % (e.args[0],  e.args[1]) 
mailer.sendMail(settings.emailAddress, error,  statement) 
sys.exit(1) 
 
for item in  statements.list: 
sql(item) 
 
If anyone knows if im doing something  silly here please let me know! Thanks!

---

