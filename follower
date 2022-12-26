function makeRequest() {
  
  var twitterService = getService_();

  params = "?max_results=1000&user.fields=created_at,location,public_metrics"
  var response = twitterService.fetch('https://api.twitter.com/2/users/${id}/followers' + params);

  if (response.getResponseCode() == 200) {

    if ( json = JSON.parse(response.getContentText()) ) {

      var ss = SpreadsheetApp.getActive().getActiveSheet();

      for (var u in json.data) {

        var user = json.data[u];

        ss.appendRow([
          user.id,
          '=hyperlink("http://twitter.com/' + user.username + '","' + user.username + '")',
          Utilities.formatDate(new Date(user.created_at), 'Etc/GMT', 'yyyy-MM-dd\'T\'HH:mm:ss'),
          user.location,
          user.public_metrics.followers_count,
          user.public_metrics.following_count,
        ]);


      }
    }
  }
  return Logger.log("Completed")
}





