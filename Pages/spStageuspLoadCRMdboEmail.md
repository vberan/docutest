Stored Procedure Stage.uspLoadCRMdboEmail {#spStageuspLoadCRMdboEmail}
-----------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboEmail] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboEmail]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboEmail] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboEmail]
            ( 
                [activityadditionalparams]
                , [activityid]
                , [activitytypecode]
                , [actualdurationminutes]
                , [actualend]
                , [actualstart]
                , [attachmentcount]
                , [attachmentopencount]
                , [baseconversationindexhash]
                , [bcc]
                , [category]
                , [cc]
                , [compressed]
                , [conversationindex]
                , [conversationtrackingid]
                , [correlationmethod]
                , [createdby]
                , [createdby_entitytype]
                , [createdbyname]
                , [createdbyyominame]
                , [createdon]
                , [createdonbehalfby]
                , [createdonbehalfby_entitytype]
                , [createdonbehalfbyname]
                , [createdonbehalfbyyominame]
                , [delayedemailsendtime]
                , [deliveryattempts]
                , [deliveryprioritycode]
                , [deliveryreceiptrequested]
                , [description]
                , [directioncode]
                , [emailreminderexpirytime]
                , [emailreminderstatus]
                , [emailremindertext]
                , [emailremindertype]
                , [emailsender]
                , [emailsender_entitytype]
                , [emailsendername]
                , [emailsenderobjecttypecode]
                , [emailsenderyominame]
                , [emailtrackingid]
                , [exchangerate]
                , [followemailuserpreference]
                , [from]
                , [Id]
                , [importsequencenumber]
                , [inreplyto]
                , [isbilled]
                , [isemailfollowed]
                , [isemailreminderset]
                , [isregularactivity]
                , [isunsafe]
                , [isworkflowcreated]
                , [lastonholdtime]
                , [lastopenedtime]
                , [linksclickedcount]
                , [llp_reportingaccountid]
                , [llp_reportingaccountid_entitytype]
                , [llp_reportingaccountidname]
                , [llp_reportingaccountidyominame]
                , [messageid]
                , [messageiddupcheck]
                , [mimetype]
                , [modifiedby]
                , [modifiedby_entitytype]
                , [modifiedbyname]
                , [modifiedbyyominame]
                , [modifiedon]
                , [modifiedonbehalfby]
                , [modifiedonbehalfby_entitytype]
                , [modifiedonbehalfbyname]
                , [modifiedonbehalfbyyominame]
                , [notifications]
                , [onholdtime]
                , [opencount]
                , [overriddencreatedon]
                , [ownerid]
                , [ownerid_entitytype]
                , [owneridname]
                , [owneridtype]
                , [owneridyominame]
                , [owningbusinessunit]
                , [owningbusinessunit_entitytype]
                , [owningteam]
                , [owningteam_entitytype]
                , [owninguser]
                , [owninguser_entitytype]
                , [parentactivityid]
                , [parentactivityid_entitytype]
                , [parentactivityidname]
                , [postponeemailprocessinguntil]
                , [prioritycode]
                , [processid]
                , [readreceiptrequested]
                , [regardingobjectid]
                , [regardingobjectid_entitytype]
                , [regardingobjectidname]
                , [regardingobjectidyominame]
                , [regardingobjecttypecode]
                , [reminderactioncardid]
                , [replycount]
                , [resco_contentstatus]
                , [resco_createdas]
                , [resco_createdfrom]
                , [resco_emailid]
                , [resco_eventid]
                , [resco_islocal]
                , [resco_snippet]
                , [resco_source]
                , [resco_statuscode]
                , [resco_threadid]
                , [safedescription]
                , [scheduleddurationminutes]
                , [scheduledend]
                , [scheduledstart]
                , [sender]
                , [sendermailboxid]
                , [sendermailboxid_entitytype]
                , [sendermailboxidname]
                , [sendersaccount]
                , [sendersaccount_entitytype]
                , [sendersaccountname]
                , [sendersaccountobjecttypecode]
                , [sendersaccountyominame]
                , [senton]
                , [serviceid]
                , [serviceid_entitytype]
                , [SinkCreatedOn]
                , [SinkModifiedOn]
                , [slaid]
                , [slaid_entitytype]
                , [slainvokedid]
                , [slainvokedid_entitytype]
                , [slainvokedidname]
                , [slaname]
                , [sortdate]
                , [stageid]
                , [statecode]
                , [statuscode]
                , [subcategory]
                , [subject]
                , [submittedby]
                , [templateid]
                , [templateid_entitytype]
                , [templateidname]
                , [timezoneruleversionnumber]
                , [to]
                , [torecipients]
                , [trackingtoken]
                , [transactioncurrencyid]
                , [transactioncurrencyid_entitytype]
                , [transactioncurrencyidname]
                , [traversedpath]
                , [utcconversiontimezonecode]
                , [versionnumber]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [activityadditionalparams] = s.[activityadditionalparams]
                , [activityid] = s.[activityid]
                , [activitytypecode] = s.[activitytypecode]
                , [actualdurationminutes] = s.[actualdurationminutes]
                , [actualend] = s.[actualend]
                , [actualstart] = s.[actualstart]
                , [attachmentcount] = s.[attachmentcount]
                , [attachmentopencount] = s.[attachmentopencount]
                , [baseconversationindexhash] = s.[baseconversationindexhash]
                , [bcc] = s.[bcc]
                , [category] = s.[category]
                , [cc] = s.[cc]
                , [compressed] = s.[compressed]
                , [conversationindex] = s.[conversationindex]
                , [conversationtrackingid] = s.[conversationtrackingid]
                , [correlationmethod] = s.[correlationmethod]
                , [createdby] = s.[createdby]
                , [createdby_entitytype] = s.[createdby_entitytype]
                , [createdbyname] = s.[createdbyname]
                , [createdbyyominame] = s.[createdbyyominame]
                , [createdon] = s.[createdon]
                , [createdonbehalfby] = s.[createdonbehalfby]
                , [createdonbehalfby_entitytype] = s.[createdonbehalfby_entitytype]
                , [createdonbehalfbyname] = s.[createdonbehalfbyname]
                , [createdonbehalfbyyominame] = s.[createdonbehalfbyyominame]
                , [delayedemailsendtime] = s.[delayedemailsendtime]
                , [deliveryattempts] = s.[deliveryattempts]
                , [deliveryprioritycode] = s.[deliveryprioritycode]
                , [deliveryreceiptrequested] = s.[deliveryreceiptrequested]
                , [description] = s.[description]
                , [directioncode] = s.[directioncode]
                , [emailreminderexpirytime] = s.[emailreminderexpirytime]
                , [emailreminderstatus] = s.[emailreminderstatus]
                , [emailremindertext] = s.[emailremindertext]
                , [emailremindertype] = s.[emailremindertype]
                , [emailsender] = s.[emailsender]
                , [emailsender_entitytype] = s.[emailsender_entitytype]
                , [emailsendername] = s.[emailsendername]
                , [emailsenderobjecttypecode] = s.[emailsenderobjecttypecode]
                , [emailsenderyominame] = s.[emailsenderyominame]
                , [emailtrackingid] = s.[emailtrackingid]
                , [exchangerate] = s.[exchangerate]
                , [followemailuserpreference] = s.[followemailuserpreference]
                , [from] = s.[from]
                , [Id] = s.[Id]
                , [importsequencenumber] = s.[importsequencenumber]
                , [inreplyto] = s.[inreplyto]
                , [isbilled] = s.[isbilled]
                , [isemailfollowed] = s.[isemailfollowed]
                , [isemailreminderset] = s.[isemailreminderset]
                , [isregularactivity] = s.[isregularactivity]
                , [isunsafe] = s.[isunsafe]
                , [isworkflowcreated] = s.[isworkflowcreated]
                , [lastonholdtime] = s.[lastonholdtime]
                , [lastopenedtime] = s.[lastopenedtime]
                , [linksclickedcount] = s.[linksclickedcount]
                , [llp_reportingaccountid] = s.[llp_reportingaccountid]
                , [llp_reportingaccountid_entitytype] = s.[llp_reportingaccountid_entitytype]
                , [llp_reportingaccountidname] = s.[llp_reportingaccountidname]
                , [llp_reportingaccountidyominame] = s.[llp_reportingaccountidyominame]
                , [messageid] = s.[messageid]
                , [messageiddupcheck] = s.[messageiddupcheck]
                , [mimetype] = s.[mimetype]
                , [modifiedby] = s.[modifiedby]
                , [modifiedby_entitytype] = s.[modifiedby_entitytype]
                , [modifiedbyname] = s.[modifiedbyname]
                , [modifiedbyyominame] = s.[modifiedbyyominame]
                , [modifiedon] = s.[modifiedon]
                , [modifiedonbehalfby] = s.[modifiedonbehalfby]
                , [modifiedonbehalfby_entitytype] = s.[modifiedonbehalfby_entitytype]
                , [modifiedonbehalfbyname] = s.[modifiedonbehalfbyname]
                , [modifiedonbehalfbyyominame] = s.[modifiedonbehalfbyyominame]
                , [notifications] = s.[notifications]
                , [onholdtime] = s.[onholdtime]
                , [opencount] = s.[opencount]
                , [overriddencreatedon] = s.[overriddencreatedon]
                , [ownerid] = s.[ownerid]
                , [ownerid_entitytype] = s.[ownerid_entitytype]
                , [owneridname] = s.[owneridname]
                , [owneridtype] = s.[owneridtype]
                , [owneridyominame] = s.[owneridyominame]
                , [owningbusinessunit] = s.[owningbusinessunit]
                , [owningbusinessunit_entitytype] = s.[owningbusinessunit_entitytype]
                , [owningteam] = s.[owningteam]
                , [owningteam_entitytype] = s.[owningteam_entitytype]
                , [owninguser] = s.[owninguser]
                , [owninguser_entitytype] = s.[owninguser_entitytype]
                , [parentactivityid] = s.[parentactivityid]
                , [parentactivityid_entitytype] = s.[parentactivityid_entitytype]
                , [parentactivityidname] = s.[parentactivityidname]
                , [postponeemailprocessinguntil] = s.[postponeemailprocessinguntil]
                , [prioritycode] = s.[prioritycode]
                , [processid] = s.[processid]
                , [readreceiptrequested] = s.[readreceiptrequested]
                , [regardingobjectid] = s.[regardingobjectid]
                , [regardingobjectid_entitytype] = s.[regardingobjectid_entitytype]
                , [regardingobjectidname] = s.[regardingobjectidname]
                , [regardingobjectidyominame] = s.[regardingobjectidyominame]
                , [regardingobjecttypecode] = s.[regardingobjecttypecode]
                , [reminderactioncardid] = s.[reminderactioncardid]
                , [replycount] = s.[replycount]
                , [resco_contentstatus] = s.[resco_contentstatus]
                , [resco_createdas] = s.[resco_createdas]
                , [resco_createdfrom] = s.[resco_createdfrom]
                , [resco_emailid] = s.[resco_emailid]
                , [resco_eventid] = s.[resco_eventid]
                , [resco_islocal] = s.[resco_islocal]
                , [resco_snippet] = s.[resco_snippet]
                , [resco_source] = s.[resco_source]
                , [resco_statuscode] = s.[resco_statuscode]
                , [resco_threadid] = s.[resco_threadid]
                , [safedescription] = s.[safedescription]
                , [scheduleddurationminutes] = s.[scheduleddurationminutes]
                , [scheduledend] = s.[scheduledend]
                , [scheduledstart] = s.[scheduledstart]
                , [sender] = s.[sender]
                , [sendermailboxid] = s.[sendermailboxid]
                , [sendermailboxid_entitytype] = s.[sendermailboxid_entitytype]
                , [sendermailboxidname] = s.[sendermailboxidname]
                , [sendersaccount] = s.[sendersaccount]
                , [sendersaccount_entitytype] = s.[sendersaccount_entitytype]
                , [sendersaccountname] = s.[sendersaccountname]
                , [sendersaccountobjecttypecode] = s.[sendersaccountobjecttypecode]
                , [sendersaccountyominame] = s.[sendersaccountyominame]
                , [senton] = s.[senton]
                , [serviceid] = s.[serviceid]
                , [serviceid_entitytype] = s.[serviceid_entitytype]
                , [SinkCreatedOn] = s.[SinkCreatedOn]
                , [SinkModifiedOn] = s.[SinkModifiedOn]
                , [slaid] = s.[slaid]
                , [slaid_entitytype] = s.[slaid_entitytype]
                , [slainvokedid] = s.[slainvokedid]
                , [slainvokedid_entitytype] = s.[slainvokedid_entitytype]
                , [slainvokedidname] = s.[slainvokedidname]
                , [slaname] = s.[slaname]
                , [sortdate] = s.[sortdate]
                , [stageid] = s.[stageid]
                , [statecode] = s.[statecode]
                , [statuscode] = s.[statuscode]
                , [subcategory] = s.[subcategory]
                , [subject] = s.[subject]
                , [submittedby] = s.[submittedby]
                , [templateid] = s.[templateid]
                , [templateid_entitytype] = s.[templateid_entitytype]
                , [templateidname] = s.[templateidname]
                , [timezoneruleversionnumber] = s.[timezoneruleversionnumber]
                , [to] = s.[to]
                , [torecipients] = s.[torecipients]
                , [trackingtoken] = s.[trackingtoken]
                , [transactioncurrencyid] = s.[transactioncurrencyid]
                , [transactioncurrencyid_entitytype] = s.[transactioncurrencyid_entitytype]
                , [transactioncurrencyidname] = s.[transactioncurrencyidname]
                , [traversedpath] = s.[traversedpath]
                , [utcconversiontimezonecode] = s.[utcconversiontimezonecode]
                , [versionnumber] = s.[versionnumber]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[email] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboEmail] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboEmail] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboEmail] WITH (NOLOCK) )
            , EndTime = GETDATE()
            , LoadDateFrom = @loadDateFrom
            , LoadDateTo = GETDATE()
            , StatusId = 3
        WHERE ThreadLogId = @ThreadLogId;

        END TRY

        BEGIN CATCH
            EXEC [dbo].[uspErrorHandler] @ThreadLogId = @ThreadLogId;
        END CATCH
            
        RETURN;
```

\[Back to stored procedure list\]\[listofprocedures\]