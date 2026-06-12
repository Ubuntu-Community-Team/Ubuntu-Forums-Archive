---
title: "Calling MS SQL Stored Procedure"
date: 2009-04-28
forum: General Help
---

### Post by ingridnav on 2009-04-28
Hi!

Using java code, I want to call a Stored Procedure on a SQL server. The appropriate drivers (FreeTDS) and data sources have been installed/created on the Ubuntu 8.04 machine, where this code is not working. The identical code is working fine on a SQL server. Calling the stored procedure directly on the SQL server also works.

The code has no problems connecting to the database and executing a Statement to INSERT data into a table. Howeer, when trying to execute a *CallableStatement* to call a stored procedure, a General Error is thrown. SQL-chaining of the exception does not provide much more detail:

SQLState: S1000
Message: General Error
Vendor ErrorCode: 0

Tracing the code through print outs, it fails on the execute() call. The code that does not work (I've left out creating the connection. Once again, this code works perfectly on a Windows machine.):

[I]String command = "{? = call spPriceFeedStart()}";
CallableStatement cstmt = con.prepareCall (command);
cstmt.registerOutParameter(1, Types.INTEGER);
cstmt.execute();  [/I]

However, if the following code is substituted, it works fine, connecting to the database and inserting the dummy data:

[I]Statement st = con.createStatement();    
st.executeUpdate("INSERT INTO TempTransfer (ID) VALUES ('TEST')");  [/I]

My questions are:
- Is anyone aware of any known issues with CallableStatements and Linux/Ubuntu/FreeTDS/etc?
- Does anyone have any other ideas or suggestions?

Thank you all in advance, your help is greatly appreciated.

---

