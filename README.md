# Linq

JavaScript 版本的 linq
====================

### 1.示例：
```JavaScript
let WorldIdentity;
(function(WorldIdentity) {
	WorldIdentity[WorldIdentity[-3] = '外挂'] = -3;
	WorldIdentity[WorldIdentity[-2] = '小号'] = -2;
	WorldIdentity[WorldIdentity[-1] = '可疑'] = -1;
	WorldIdentity[WorldIdentity[0] = '普通'] = 0;
	WorldIdentity[WorldIdentity[1] = '合伙'] = 1;
})(WorldIdentity || (WorldIdentity = {}));
Core.GameServer.Load(null, p => {
	if (!p.result) {
		alert(p.data, 'initialize page error:');
		return;
	}

	let sltIdentity = $('#slt_world_identity');
	let sltServer = $('#slt_server');
	let keys = Object.getOwnPropertyNames(WorldIdentity);
	Linq.where(keys, p => !isNaN(p))
		.select(p => Number(p))
		.orderBy(p => p)
		.forEach(p => sltIdentity.append('<option value="' + p + '">' + WorldIdentity[p] + '</option>'));
	Linq.orderByDescending(p.data, p => p.IsLegal)
		.thenBy(p => p.ID)
		.forEach(p => sltServer.append('<option value="' + p.ID + '">' + p.Name + '</option>'));

	sltIdentity.val(0);
});
```