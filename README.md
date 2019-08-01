# How to use

`npm install` and `open index.html in browser`

## js es6 class 练手
>  用import,export, class等es6语法来编写js， 然后使用babel编译，使用browserify打包， 让你简单快速的用纯es6在本地练习js以及练手html。

# js 代码
```javascript 
const BaseContent = require("./components/BaseContent");
const JobCard = require("./components/JobCard");

class Job extends BaseContent{
    constructor(initData){
        super(initData);
        const { dataList = []} = initData;
        this.itemList = dataList;
    }
    
    createContent() {
        let jobElem = document.createElement("div");
        jobElem.classList.add("job-content");
        let groupBy = [];
        for(var i=0,len=this.itemList.length;i<len;i+=3){
            groupBy.push(this.itemList.slice(i,i+3));
        }     
        groupBy.map((items)=>{
            let itemRow = document.createElement("div");
            itemRow.classList.add("recruitment-item-row");
            items.forEach((i)=>{
                let jobPaper = new JobCard(i);
                let divElem = jobPaper.init();
                itemRow.appendChild(divElem);
            })  
            jobElem.appendChild(itemRow);
        });
        return jobElem;
    }
}

module.exports = Job;
```
