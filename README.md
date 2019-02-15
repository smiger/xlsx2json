### xlsx2json
> 根据项目需要，通过开源项目([koalaylj/xlsx2json](https://github.com/koalaylj/xlsx2json.git))改写。让excel支持复杂的json格式, 将xlsx文件转成json。

### 主要区别
* 实现sheet多层级嵌套
* sheet字段类型指定

### 使用说明
* 目前只支持.xlsx格式，不支持.xls格式。
* 本项目是基于nodejs的，所以需要先安装nodejs环境。
* 执行命令
```bash
# Clone this repository
git clone https://github.com/koalaylj/xlsx2json.git
# Go into the repository
cd xlsx2json
# Install dependencies
npm install
```

* 配置config.json
```javascript
{
    "xlsx": {
        /**
         * 表头所在的行，第一行是表头，第二行是描述，第三行是类型
         */
        "head": 1,
        /**
         * 主表
         */
        "master": "Sheet1",
        /**
         * xlsx文件所在的目录
         * glob配置风格
         */
        "src": "./excel/**/[^~$]*.xlsx",

        /**
         * 导出的json存放的位置
         */
        "dest": "./json"
    },

    /**
     * 是否导出d.ts（for typescript）
     * 一张表格只导出一个d.ts文件
     * true:生成d.ts，false:不生成
     */
    "ts":false,

    "json": {
      /**
       * 导出的json是否需要压缩
       * true:压缩，false:不压缩(便于阅读的格式)
       */
      "uglify": false
    }
}
```
* 执行`export.sh|export.bat`即可将`./excel/*.xlsx` 文件导成json并存放到 `./json` 下。json名字以excel的sheet名字命名。
