---
title: "WINE &amp; Freetds &amp;  MSSQL"
date: 2012-02-14
forum: Desktop Environments
---

### Post by gapete on 2012-02-14
hi to all,

im really stuck.

I cant do an app to work with ODBC.

UBUNTU 11.10

I installed freeTDS an unixODBC, tsql and isql both connect and i can do a select........

so i exec an app in wine but i cant connect to mssql. 

this errors with WINEDEBUG=odbc wine cmd

then exec my app

> trace: odbc:llMain Initializing or Finalizing proxy ODBC: 0x3d700000,1,(nil)
trace: odbc allMain Loading ODBC...
trace: odbc:ODBC_LoadDriverManager 
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLAllocHandleStd: /usr/lib/libtdsodbc.so: undefined symbol: SQLAllocHandleStd
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLBrowseConnect: /usr/lib/libtdsodbc.so: undefined symbol: SQLBrowseConnect
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLBrowseConnectW: /usr/lib/libtdsodbc.so: undefined symbol: SQLBrowseConnectW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLBulkOperations: /usr/lib/libtdsodbc.so: undefined symbol: SQLBulkOperations
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLColAttributeW: /usr/lib/libtdsodbc.so: undefined symbol: SQLColAttributeW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLColAttributesW: /usr/lib/libtdsodbc.so: undefined symbol: SQLColAttributesW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLColumnPrivilegesW: /usr/lib/libtdsodbc.so: undefined symbol: SQLColumnPrivilegesW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLColumnsW: /usr/lib/libtdsodbc.so: undefined symbol: SQLColumnsW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLConnectW: /usr/lib/libtdsodbc.so: undefined symbol: SQLConnectW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDataSources: /usr/lib/libtdsodbc.so: undefined symbol: SQLDataSources
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDataSourcesW: /usr/lib/libtdsodbc.so: undefined symbol: SQLDataSourcesW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDescribeColW: /usr/lib/libtdsodbc.so: undefined symbol: SQLDescribeColW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDescribeParam: /usr/lib/libtdsodbc.so: undefined symbol: SQLDescribeParam
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDriverConnectW: /usr/lib/libtdsodbc.so: undefined symbol: SQLDriverConnectW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDrivers: /usr/lib/libtdsodbc.so: undefined symbol: SQLDrivers
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLDriversW: /usr/lib/libtdsodbc.so: undefined symbol: SQLDriversW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLErrorW: /usr/lib/libtdsodbc.so: undefined symbol: SQLErrorW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLExecDirectW: /usr/lib/libtdsodbc.so: undefined symbol: SQLExecDirectW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLForeignKeysW: /usr/lib/libtdsodbc.so: undefined symbol: SQLForeignKeysW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetConnectAttrW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetConnectAttrW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetConnectOptionW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetConnectOptionW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetCursorNameW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetCursorNameW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetDescFieldW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetDescFieldW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetDescRecW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetDescRecW
vODBC_LoadDMFunctions Failed to load SQLGetDiagFieldW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetDiagFieldW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetDiagRecW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetDiagRecW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetInfoW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetInfoW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetStmtAttrW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetStmtAttrW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLGetTypeInfoW: /usr/lib/libtdsodbc.so: undefined symbol: SQLGetTypeInfoW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLNativeSqlW: /usr/lib/libtdsodbc.so: undefined symbol: SQLNativeSqlW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLPrepareW: /usr/lib/libtdsodbc.so: undefined symbol: SQLPrepareW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLPrimaryKeysW: /usr/lib/libtdsodbc.so: undefined symbol: SQLPrimaryKeysW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLProcedureColumnsW: /usr/lib/libtdsodbc.so: undefined symbol: SQLProcedureColumnsW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLProceduresW: /usr/lib/libtdsodbc.so: undefined symbol: SQLProceduresW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSetConnectAttrW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSetConnectAttrW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSetConnectOptionW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSetConnectOptionW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSetCursorNameW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSetCursorNameW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSetDescFieldW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSetDescFieldW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSetStmtAttrW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSetStmtAttrW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLSpecialColumnsW: /usr/lib/libtdsodbc.so: undefined symbol: SQLSpecialColumnsW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLStatisticsW: /usr/lib/libtdsodbc.so: undefined symbol: SQLStatisticsW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLTablePrivilegesW: /usr/lib/libtdsodbc.so: undefined symbol: SQLTablePrivilegesW
warn: odbc:ODBC_LoadDMFunctions Failed to load SQLTablesW: /usr/lib/libtdsodbc.so: undefined symbol: SQLTablesW
trace: odbc:SQLAllocEnv 
trace: odbc:SQLAllocEnv Returns ret=0, Env=7c804938
trace: odbc:ODBC_ReplicateODBCInstToRegistry Driver settings are not currently replicated to the registry
trace: odbc:SQLDrivers 
trace: odbc:ODBC_ReplicateODBCInstToRegistry Error -1 enumerating drivers
warn: odbc:ODBC_ReplicateODBCInstToRegistry May not have replicated all ODBC drivers to the registry
trace: odbc:SQLDataSources EnvironmentHandle = 0x7c804938
trace: odbc:ODBC_ReplicateODBCToRegistry Error -1 enumerating system datasources
warn: odbc:ODBC_ReplicateODBCToRegistry May not have replicated all system ODBC DSNs to the registry
trace: odbc:SQLDataSources EnvironmentHandle = 0x7c804938
trace: odbcODBC_ReplicateODBCToRegistry Error -1 enumerating user datasources
warn: odbc:ODBC_ReplicateODBCToRegistry May not have replicated all user ODBC DSNs to the registrymy freetds.conf. odbc.ini, odbcinst.ini

freetds.conf
> 
[global]
        # TDS protocol version
        tds version = 7.1
        text size = 64512
[TDS]
        host = 192.168.0.5
        port = 1433
        tds version = 7.1odbc.ini
> [prueba]
Driver          = MSSQLServer
Servername      = TDS
Database        = nueva2
UID             = unbian
PWD             = unbian/etc/odbcinst.ini
> [MSSQLServer]
Driver          =/usr/lib/libtdsodbc.so
Setup           =/usr/lib/libtdsS.soi dont know what more i can do to solve the problem.

thx in advance.

---

### Post by gapete on 2012-02-15
nothing???

---

