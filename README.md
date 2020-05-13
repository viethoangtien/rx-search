![alt text](https://user-images.githubusercontent.com/43170922/81789859-c424c600-952e-11ea-8dfe-fb2ae82c82a7.PNG)
## Implement Search Using Rxjava
**- Debounce:**
Here, the debounce operator is used with a time constant. The debounce operator handles the case when the user types “a”, “ab”, “abc”, in a very short time. So there will be too much network calls. But the user is finally interested in the result of the search “abc”. So, you must discard the results of “a” and “ab”. Ideally, there should be no network calls for “a” and “ab” as the user typed those in very short time. So, the debounce operator comes to the rescue. The debounce will wait for the provided time for doing anything, if any other search query comes in between that time, it will ignore the previous item and start waiting for that time again with the new search query. If nothing new comes in that given constant time, it will proceed with that search query for further processing. So, debounce only emit an item from an Observable if a particular timespan has passed without it emitting an another item.

**- Filter:**
The filter operator is used to filter the unwanted string like empty string in this case to avoid the unnecessary network call

**- DistinctUntilChanged:**
The distinctUntilChanged operator is used to avoid the duplicate network calls. Let say the last on-going search query was “abc” and the user deleted “c” and again typed “c”. So again it’s “abc”. So if the network call is already going on with the search query “abc”, it will not make the duplicate call again with the search query “abc”. So, distinctUntilChanged suppress duplicate consecutive items emitted by the source Observable
